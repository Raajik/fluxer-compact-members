# Fluxer compact sidebars

A custom CSS snippet for Fluxer (https://fluxer.app). It shrinks the member
list to a narrow column of avatars. It also shrinks the channel list to the
server name. Hovering a shrunk column expands it over the chat.

The snippet lives in `compact-members.css`. It holds all the behaviors,
because Fluxer loads them as one Quick CSS block.

## Behavior

### Member list

- On desktop widths (768px and up), the member list is about 3.75rem wide
  instead of 16.5rem.
- Each member row shows only the avatar, centered. The avatar keeps its status
  dot and typing indicator.
- Names, custom statuses, owner crowns and bot tags are hidden.
- Offline members stay faded (Fluxer's own styling), so you can still see at a
  glance who is around.
- Group headers ("Online — 5", role names) show a thin divider line instead of
  their text, so groups are still separated.
- Hovering the list expands it to the normal 16.5rem list, with names,
  statuses and group headers, drawn over the chat area. The chat does not move
  or reflow. Moving the mouse out collapses it again.
- Clicking an avatar still opens the user's profile popout, and right-clicking
  still opens the context menu.
- The mobile layout is unchanged.

### Channel list

- On desktop widths (768px and up), in a community channel, the channel
  sidebar has no width. A small control floats at the top left. It shows the
  server name and opens the channel list on hover.
- Hovering or focusing the server name shows the normal 20rem channel list as
  a dropdown over the chat. The chat does not move or reflow. Moving the mouse
  out collapses it again.
- The chat header and the composer keep clear of the floating server name and
  the bottom-left user panel.
- Clicking the server name still opens the community menu. Channel clicks and
  the channel context menu still work while the list is open.
- Direct message, Discovery and Favorites sidebars keep their width.

### Voice connection panel

- On desktop widths (768px and up), the "In voice chat" panel above the
  bottom-left user panel is hidden. It takes no vertical space.
- Hovering or focusing the bottom-left user panel shows the panel over the
  chat. Moving the pointer out hides it again.
- The user panel and the chat do not move.

### Talking ring on your own avatar

- While you talk in a voice channel, your avatar in the bottom-left user panel
  and your avatar in the member list get the same green ring that Fluxer
  shows on talking voice avatars.
- Other members get no ring. Their talking rows do not show the user, and CSS
  cannot compare user IDs.
- The ring goes away when you stop talking.
- Nothing to set up. The snippet works for every user as is.
- Fluxer has no "I am talking" marker. Your own voice row in the channel list
  has a "current connection" class only while you are silent. Fluxer removes
  it while you talk. So the ring shows when all of these are true:
  - you are in a voice channel,
  - a voice row in the channel list shows talking,
  - no voice row has the "current connection" class.
- Your voice channel must show in the channel list (also while the list is
  hidden). If its category is collapsed, the ring does not show.
- Known false ring: you view a different server while you are in voice, and
  somebody talks in a voice channel of that server.

## Constraints

- Pure CSS, pasted into User Settings → Look & feel → Theme → "Open theme
  studio…" → Quick CSS. No plugin injector or client mod needed.
- Select elements only by Fluxer's `data-flx` attributes, which the project
  keeps stable for theming. Never select by the hashed CSS-module class names.
  One exception: the talking state has no `data-flx` marker, so the talking
  ring matches the class-name parts `__participantRowSpeaking___` and
  `__participantRowCurrentConnection___`. Fluxer builds module class names as
  `[name]__[local]___[hash]`, so these parts have no hash.
- Do not change member row heights. The member list is virtualized, and it
  positions rows from fixed pixel heights in JS (`MEMBER_LIST_ITEM_HEIGHT_PX`,
  `MEMBER_LIST_GROUP_HEADER_HEIGHT_PX`). Changing heights in CSS would make
  rows overlap or leave gaps.
- The channel list is not virtualized, so it is safe to hide with `visibility`
  while the column is collapsed.
- Built against fluxerapp/fluxer commit 2ffe8f3 (2026-10-12).

## Done when

- Both sidebars are narrow in a community channel.
- There is no horizontal scrollbar, and avatars are not clipped.
- Group separation is visible, and offline members look faded.
- Scrolling a large member list shows no overlapping rows or gaps.
- Clicking a member avatar opens the profile popout.
- Hovering the member list expands it with names, and the chat text does not
  shift sideways.
- Hovering the channel sidebar shows the channel list over the chat, and the
  chat text does not shift sideways.
- The community menu opens from the floating server name.
- The DM, Discovery and Favorites sidebars look unchanged.
- The "In voice chat" panel is not visible while the pointer is away from the
  bottom-left user panel.
- Hovering the bottom-left user panel shows the panel, and the chat does not
  move.
- The voice controls in the panel still work while the panel is shown.
- In a voice channel, your bottom-left avatar and your member list avatar
  have a green ring while you talk. It has no ring while you are silent, also while others talk.

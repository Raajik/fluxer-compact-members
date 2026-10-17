# Fluxer compact sidebars

A custom CSS snippet for Fluxer (https://fluxer.app). It shrinks the member
list to a narrow column of avatars. It also shrinks the channel list to the
server name. Hovering a shrunk column expands it over the chat.

The snippet lives in `compact-members.css`. It holds both behaviors, because
Fluxer loads them as one Quick CSS block.

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
  sidebar is about 7rem wide instead of 20rem.
- The collapsed column shows the server name header only. The header packs
  the name and the caret at the left, so no empty space shows. The channel
  list is hidden.
- Hovering the sidebar expands it to the normal 20rem channel list, drawn over
  the chat area. The chat does not move or reflow. Moving the mouse out
  collapses it again.
- Clicking the server name still opens the community menu. Channel clicks and
  the channel context menu still work while the list is open.
- Direct message, Discovery and Favorites sidebars keep their width.

## Constraints

- Pure CSS, pasted into User Settings → Look & feel → Theme → "Open theme
  studio…" → Quick CSS. No plugin injector or client mod needed.
- Select elements only by Fluxer's `data-flx` attributes, which the project
  keeps stable for theming. Never select by the hashed CSS-module class names.
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
- The community menu opens from the server name in the collapsed column.
- The DM, Discovery and Favorites sidebars look unchanged.

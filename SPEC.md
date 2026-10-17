# Fluxer compact member list

A custom CSS snippet for Fluxer (https://fluxer.app) that shrinks the Members
sidebar to a narrow column of avatars.

## Behavior

- On desktop widths (768px and up), the Members sidebar is about 3.75rem wide
  instead of 16.5rem.
- Each member row shows only the avatar, centered. The avatar keeps its status
  dot and typing indicator.
- Names, custom statuses, owner crowns and bot tags are hidden.
- Offline members stay faded (Fluxer's own styling), so you can still see at a
  glance who is around.
- Group headers ("Online — 5", role names) show a thin divider line instead of
  their text, so groups are still separated.
- Hovering the list expands it to the normal 16.5rem list, with names,
  statuses and group headers, drawn over the chat area. The chat does not
  move or reflow. Moving the mouse out collapses it again.
- Clicking an avatar still opens the user's profile popout, and right-clicking
  still opens the context menu.
- The mobile layout is unchanged.

## Constraints

- Pure CSS, pasted into User Settings → Look & feel → Theme → "Open theme
  studio…" → Quick CSS. No plugin injector or client mod needed.
- Select elements only by Fluxer's `data-flx` attributes, which the project
  keeps stable for theming. Never select by the hashed CSS-module class names.
- Don't change row heights. The member list is virtualized, and it positions
  rows from fixed pixel heights in JS (`MEMBER_LIST_ITEM_HEIGHT_PX`,
  `MEMBER_LIST_GROUP_HEADER_HEIGHT_PX`). Changing heights in CSS would make
  rows overlap or leave gaps.
- Built against fluxerapp/fluxer commit 2ffe8f3 (2026-10-12).

## Done when

- The sidebar is a narrow avatar column in a server channel and in a group DM.
- There's no horizontal scrollbar, and avatars aren't clipped.
- Group separation is visible, and offline members look faded.
- Scrolling a large server's member list shows no overlapping rows or gaps.
- Clicking an avatar opens the profile popout.
- Hovering expands the list over the chat with names showing, and the chat
  text does not shift sideways. Leaving collapses it.

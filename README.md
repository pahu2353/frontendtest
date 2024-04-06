# Chess.com Frontend Programming Challenge
My submission for the chess.com frontend programming challenge! Please feel free to take a look and try everything out for yourself [here](https://chesscomfrontend.vercel.app/)!

![image](https://github.com/pahu2353/chesscomfrontend/assets/50181097/df652ef9-4ef8-4c0f-8800-cd02c2487a91)


## Application Requirements
We were tasked to:
1. Create a page with a chessboard and a sidebar.
2. On desktop devices the sidebar should be positioned to the right of the chessboard.
3. On mobile devices the sidebar should be positioned below the chessboard.
4. The chessboard should resize responsively to consume available space.
5. Clicking a chessboard square should highlight the square.
6. Keep track of which squares are clicked and the order in which they're clicked.
7. Display the information collected from step 6 in the sidebar.

## Design Notes
I wanted to replicate the design of a chess.com board as much as possible; thus, the colours/styling, the spacing, and the design elements were all themed in a chess.com-esque style. I originally used a .png of the chess.com logo, but I created my own "chessdotcom" logo for the final product to avoid copyright infringement.

Additional features (beyond the application requirements) that were added were:
- The ability to unhighlight previously highlighted squares by clicking on them again
- A toggle ("Show Currently Clicked/Hide Currently Clicked") to view currently highlighted squares, in addition to previous clicks
- In-board coordinates in the style of a chess.com board

I interpreted that the 'total history' as required in the instructions (#6) was only referring to highlighting clicks, not unhighlighting clicks — the total history in my completed application only displays highlighted clicks. However, it is able to log both!

## App Structure
- `App.vue`: App entrypoint — contains overarching methods and styles like addHistory and container flexbox.
- Components:
  - `ChessBoard`: Renders 8x8 grid and emits data from `BoardSquares`.
  - `BoardSquares`: Reusable sub-component of `ChessBoard`; handles labels (in-board coordinates).
  - `SideBar`: Displays previously highlighted and currently highlighted squares.

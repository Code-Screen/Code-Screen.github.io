```js
{
  // The game state (managed by you).
  G: {},

  // Read-only metadata (managed by the framework).
  ctx: {
    turn: 0,
    currentPlayer: '0',
    numPlayers: 2,
  }
}
```

These state objects are passed around everywhere and maintained
on both client and server seamlessly. The state in `ctx` is
incrementally adoptable, meaning that you can manage all the
state manually in `G` if you so desire.

!> `ctx` contains other fields not shown here that complex games
can take advantage of, including support for game phases and complex
turn orders.

### Moves

These are functions that tell the framework how to change `G`
when a particular game move is made. They must not depend on
external state or have any side-effects (except modifying `G`).
See the guide on [Immutability](immutability.md) for how
immutability is handled by the framework.

```js
moves: {
  drawCard: (G, ctx) => {
    const card = G.deck.pop();
    G.hand.push(card);
  },

  ...
}
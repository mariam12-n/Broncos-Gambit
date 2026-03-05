Host -->> Engine: "position startpos move e2e4 e7e5 ..."
    activate Engine
    Engine ->> Parser: parse "position ..." (detect startpos (or fen))
    Parser ->> Position: create Position (start Pos (or fromFEN))
    loop for each move token
        Parser ->> MoveOBj: Move.fromUci("e2e4")
        MoveObj -->> Parser: Move object
        Parser ->> Position: Position = Position.makeMove(Move)
    end
    Engine -->> Host: (no response required)
    deactivate Engine

```mermaid
sequenceDiagram
	autonumber
	actor P as Person
	participant ATM
	participant BS as Bank Server

	Note right of P: Any living creature
	%% this is a comment
	P->>+ATM: Insert Card
	ATM->>+BS: VerifyCard(cardId: string)
	alt if card is valid
	BS-->>ATM: res:true
	ATM->>P: Request PIN
	else else
	BS-->>-ATM: res: false
	ATM->>-P: Eject Card
	end
	
	loop Every 5 min
		ATM->>P: Are you still here
	end
```

```mermaid
sequenceDiagram
    actor Verifier
    actor Good Generator
    create participant hypercert
    Good Generator->>hypercert: mint impact goal
    actor Change Code
    hypercert-->Change Code: review impact goal
    create participant Token Bound Account
    Change Code->>Token Bound Account: deploy TBA
    actor donor
    loop
        donor->>Token Bound Account: send $
        Token Bound Account->>donor: mint IOU
            Token Bound Account->>Good Generator: remit funding received
    end
    loop
        Good Generator-->Good Generator: implement project
        Good Generator->>hypercert: submit evidence
        Verifier-->hypercert: review evidence
        Change Code-->hypercert: determine quantity
        Change Code->>Token Bound Account: mint Change Credits
    end
    Loop
        donor->>Token Bound Account: return IOUs
        Token Bound Account->>donor: receive Change Credits
    end
```


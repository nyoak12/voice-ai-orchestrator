DRAFT: The goal of this project is to take what I learned from the previous ai voice bot project and redo my approach from the ground up as a result of my findings.

my previous voice bot architecture:
    
    user input -> SST -> ai model -> TTS -> output 

    positives:
        -used open source model 
        -free to run locally on computer
    limitations:
        -lacked reasoning ability 
        -poor sales agent performance
        -unable to support business operations

hypothesis:
    new architecture will be more effective by creating a deterministic work flow that seperates tasks and reduces scope for light weight ai models.


    user input 
    -> SST 
    -> controller
        |
        state -> source of truth (memory)
        |
        extraction -> low temperature model
        |
        state update
        |
        decision logic (code + rules) -> returns ACTION
        |
        strategy (behavior)
        |
        retrieval -> knowledge base / search system + ai model(optional summarizer)
        |
        response generation -> high temperature model
    -> TTS
    -> output


clarification: ACTION returns (possible enum):
    - EXTRACT
    - ASK_FOR_INFO
    - ANSWER_QUESTION
    - RETRIEVE_KNOWLEDGE
    - GENERATE_RESPONSE
    - COMPLETE


Technologies:

    c++ to keep latency low and controlled

    whisper (STT)
    port audio (microphone/speaker)
    ollama (open source models run locally)

    makefile -> c++ build system

Design Patterns:
        -> builder
        -> controller
        -> strategy
        -> state
        -> factory


current status:
- [x] Architecture design
- [ ] Project structure (in progress)
- [ ] Controller implementation (in progress)
- [ ] State management
- [ ] Model integration

next steps:
    1. make project file structure to reflect architecture in draft

    2. Implement controller with string outputs to simulate the flow of tasks and design pattern organization.
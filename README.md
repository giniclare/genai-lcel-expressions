## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:

### DESIGN STEPS:

#### STEP 1:
Environment Setup & Configuration: Configure system environment bindings using dotenv variables to securely manage API keys. Mask credentials away from public source files to satisfy secure repository guidelines.
#### STEP 2:
Component Architecture Definition: Instanciate the separate phases of our LangChain workflow engine:

Prompt Definition: Create a ChatPromptTemplate using exactly two target criteria keys: {ingredient} and {meal_type}.
Inference Engine Initialization: Instantiate a ChatOpenAI chat completions instance targeting a specific fast-response model snapshot.
Response Processing Phase: Instantiate a clean structural sequence via StrOutputParser to isolate content text blocks from payload metadata headers.
#### STEP 3:
Workflow Pipeline Graph Composition: Form the cohesive operational chain using explicit pipe syntax (|). Run performance evaluation loops across single processing items (.invoke()) and multiple elements concurrently (.batch()) to verify complete multi-parameter stability.
### PROGRAM:
```
import os
from getpass import getpass

from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_openai import ChatOpenAI

if not os.getenv("OPENAI_API_KEY"):
    os.environ["OPENAI_API_KEY"] = getpass("Enter your OpenAI API key: ")

prompt = ChatPromptTemplate.from_template(
    "Explain {topic} in simple English for {audience}. "
    "Give a short explanation and one practical example."
)

model = ChatOpenAI(model="gpt-4.1-mini", temperature=0)
output_parser = StrOutputParser()
chain = prompt | model | output_parser
result = chain.invoke({
    "topic": "BTS",
    "audience": "ARMY"
})

# Step 7: Display the result
print("LCEL OUTPUT:")
print(result)

```
### OUTPUT:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bc2051bb-a362-46a3-a832-304feeb1f24d" />

### RESULT:
Thus, a modernized declarative LangChain Expression Language (LCEL) application pipeline successfully accepted multiple custom prompt constraints to dynamically generate contextually accurate recipes, satisfying all code validation constraints with masked API keys.

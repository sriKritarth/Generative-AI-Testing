# GenAI Model Testing Log

This document logs observations from testing two Large Language Models (LLMs): OpenAI `gpt-4o` and Groq `deepseek-r1-distill-llama-70b`. The tests were conducted using various prompts as detailed in the `prompt_test.ipynb` notebook.

## Model: OpenAI `gpt-4o`

| Prompt Category         | Prompt Used                                                                  | Output Summary                                                                                                                               | Accuracy | Latency/Performance Notes | Observed Bugs/Glitches | Rating (out of 10) | Final Notes/Improvement Ideas          |
| :---------------------- | :--------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------- | :------- | :------------------------ | :--------------------- | :----------------- | :------------------------------------- |
| Factual Question        | "What is the speed of light in a vacuum?"                                    | Correctly stated speed of light (299,792,458 m/s or ~300,000 km/s).                                                                          | High     | ~2 sec          | None                   | 9                  | Clear and concise.                     |
| Creative Writing        | "A bustling city under the sky." (creative_prompt)                           | Wrote a story about an artist (Elara) in a vibrant city (Lumina), capturing the sunset and city lights.                                      | High     | ~2 sec           | None                   | 9                  | Imaginative and well-written.          |
| Long Input/Complex Data | Analyze and summarize text on tech history (computers, programming, internet). | Summarized tech history, listed themes (computer evolution, programming languages, internet impact), noted lack of stats in input, posed AI/ML question. | High     | ~3 sec         | None                   | 9                  | Comprehensive analysis.                |
| Code Base Prompt        | Translate Python: `print('Hello, World!')` to JavaScript.                    | Translated Python `print` to JavaScript `console.log` correctly.                                                                             | High     |~3 sec         | None                   | 10                 | Correct and direct.                    |

## Model: Groq `deepseek-r1-distill-llama-70b`

| Prompt Category         | Prompt Used                                                                  | Output Summary                                                                                                                                                           | Accuracy | Latency/Performance Notes | Observed Bugs/Glitches                     | Rating (out of 10) | Final Notes/Improvement Ideas                                   |
| :---------------------- | :--------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------- | :------------------------ | :----------------------------------------- | :----------------- | :-------------------------------------------------------------- |
| Factual Question        | "What is the speed of light in a vacuum?"                                    | Correctly stated speed of light (~299,792 km/s or 300,000,000 m/s). Output preceded by `<think>` block detailing reasoning.                                                | High     |~2 sec          | Output includes `<think>` meta-commentary. | 8                  | Answer correct; `<think>` block adds verbosity.                 |
| Creative Writing        | "A bustling city under the sky." (creative_prompt)                           | Wrote a story about a bustling city square with diverse activities. Output preceded by `<think>` block detailing story generation.                                           | High     | ~2 sec          | Output includes `<think>` meta-commentary. | 8                  | Good story; `<think>` block not ideal for final output.         |
| Long Input/Complex Data | Analyze and summarize text on tech history (computers, programming, internet). | Summarized tech history, themes (innovation, languages, internet), data points (first computer, WWW, social media), posed future trends question. Output preceded by `<think>` block. | High     | ~4 sec         | Output includes `<think>` meta-commentary. | 8                  | Thorough analysis; `<think>` block adds verbosity.              |
| Code Base Prompt        | Translate Python: `print('Hello, World!')` to JavaScript.                    | Translated Python `print` to JavaScript `console.log` with explanation. Output preceded by `<think>` block.                                                                 | High     | ~3 sec         | Output includes `<think>` meta-commentary. | 8                  | Correct translation; explanation good but verbose due to `<think>`. |

**Note:**
- **Accuracy:** Based on the factual correctness and relevance of the response to the prompt.
- **Latency/Performance Notes:** "to be determined" as direct measurement was not part of this observation.
- **Rating:** A subjective score reflecting overall quality, conciseness, and directness of the response.
- **Observed Bugs/Glitches:** The `<think>` tags in Groq's model output are noted as a characteristic rather than a bug, but they affect the usability of the raw output.


# AI Interview Assistant Prompt Library

This project implements an AI Interview Assistant using LangChain, demonstrating the use of different language models (GPT-4 and Ollama's llama3) for conducting mock interviews. The system is designed to adapt its interview style based on the candidate's experience level, the type of skills being assessed, and the desired tone of the conversation.

## Project Structure

- `test.ipynb`: Main Jupyter notebook containing the implementation
- `README.md`: This documentation file

## Features

### 1. Customizable Interview Parameters

The system accepts three main parameters to customize each interview session:
- **Level**: beginner or advanced
- **Categorization**: technical, creative, or analytical
- **Tone**: formal, casual, or funny

### 2. Interview Components

Each interview session includes:
1. Introduction
2. "Tell me about yourself" question
3. Follow-up questions
4. Detailed feedback
5. Closing remarks

### 3. Model Integration

The project demonstrates integration with two different LLM models:
- OpenAI's GPT-4
- Ollama's llama3 (local model)

## Model Comparison

### Prompt and Output Analysis

#### Test Case 1: Beginner Technical Interview (Formal Tone)

| Aspect | GPT-4 | Ollama (llama3) |
|--------|-------|-----------------|
| **Introduction** | "Good day. I am an AI Interview Assistant, and I am here to conduct a mock interview with you. The purpose of this session is to help you practice and refine your interview skills, particularly focusing on technical aspects at a beginner level. Let us begin." | "I'm pleased to assist you with this mock interview. As an AI Interview Assistant, my goal is to help you practice your interview skills and provide constructive feedback." |
| **Initial Question Style** | Structured, with context: "Could you please introduce yourself? I am particularly interested in hearing about your background in technology, any relevant skills you have acquired, and what has motivated you to pursue a career in this field." | Direct and simple: "Let's get started! Can you begin by introducing yourself and telling me a little bit about your background and experience in the technical field?" |
| **Follow-up Questions** | 1. Specific technical focus: "Could you elaborate on any specific programming languages or tools you have started learning...?"<br>2. Project-based: "Can you describe a project or assignment...?"<br>3. Learning approach: "How do you approach learning new technical concepts...?" | (Limited to initial interaction in the example) |
| **Feedback Structure** | Comprehensive with categories:<br>- Clarity and Conciseness<br>- Technical Relevance<br>- Level Appropriateness<br>- Areas for Improvement<br>- Strengths Demonstrated | Brief acknowledgment and basic guidance |
| **Response Length** | ~400-500 words | ~100-150 words |

#### Test Case 2: Advanced Creative Interview (Formal Tone)

| Aspect | GPT-4 | Ollama (llama3) |
|--------|-------|-----------------|
| **Introduction** | "Good day. I am your AI Interview Assistant, and I am here to facilitate a mock interview designed to enhance your interview skills. This session will focus on the creative category, and given your advanced level of experience, we will delve into more complex scenarios and questions." | "I'm delighted to assist you in this advanced-level creative mock interview. As an AI Interview Assistant, my primary goal is to simulate a real-world interview experience." |
| **Initial Question Style** | Sophisticated and specific: "Please introduce yourself, highlighting your journey and achievements in the creative field. Given your advanced experience, I am particularly interested in understanding how your background has shaped your creative vision and approach." | General with creative focus: "Can you start by introducing yourself and sharing your background, highlighting any relevant experiences or achievements that showcase your creative skills?" |
| **Follow-up Questions** | 1. Portfolio-focused: "Could you elaborate on a specific project that best exemplifies your creative expertise?"<br>2. Innovation-centered: "Can you discuss a time when you introduced a novel idea...?"<br>3. Industry insight: "How do you stay ahead of emerging trends...?" | (Limited to initial interaction in the example) |
| **Feedback Structure** | Detailed analysis of:<br>- Creative approach<br>- Innovation examples<br>- Portfolio discussion<br>- Strategic thinking<br>- Future vision | Basic structure with note-taking mention |
| **Response Length** | ~600-700 words | ~150-200 words |

#### Test Case 3: Beginner Analytical Interview (Casual Tone)

| Aspect | GPT-4 | Ollama (llama3) |
|--------|-------|-----------------|
| **Introduction** | [Not shown in the example] | "Let's get started with this mock interview! I'm your AI Interview Assistant, and I'll be guiding you through a simulated conversation. Don't worry; it's just for practice, so feel free to relax and be yourself." |
| **Initial Question Style** | [Not shown in the example] | Casual and encouraging: "Can you tell me about yourself? As an analytical beginner, I'd love to hear about your background, interests, or any relevant experiences that might give us a starting point for our discussion?" |
| **Tone Adaptation** | [Not shown in the example] | Successfully maintains casual tone: "Remember, this is a casual conversation, so don't worry too much about perfection. Just share what comes naturally!" |
| **Response Length** | [Not shown in the example] | ~100-150 words |

### Key Differences in Implementation

| Feature | GPT-4 | Ollama (llama3) |
|---------|-------|-----------------|
| **Response Structure** | Hierarchical, well-organized sections | Linear, conversational flow |
| **Question Complexity** | Varies based on level and category | Generally consistent, simpler structure |
| **Context Retention** | Maintains context throughout the interview | Focuses on immediate interaction |
| **Tone Adaptation** | Precise adaptation to formal/casual/funny | Basic tone adjustments |
| **Technical Depth** | Adjusts technical depth based on level | More uniform technical depth |
| **Feedback Style** | Structured, multi-point feedback | Brief, general feedback |
| **Resource Usage** | Requires API calls, higher latency | Local execution, lower latency |
| **Cost Implications** | Pay per token | Free, local deployment |

## Usage

1. **Environment Setup:**
   ```python
   from dotenv import load_dotenv
   load_dotenv()
   ```

2. **GPT-4 Implementation:**
   ```python
   from langchain_openai import ChatOpenAI
   from langchain_core.prompts import PromptTemplate
   from langchain_core.output_parsers import StrOutputParser

   model = ChatOpenAI(model="gpt-4", temperature=0.0)
   ```

3. **Ollama Implementation:**
   ```python
   from langchain_ollama.llms import OllamaLLM
   model_ollama = OllamaLLM(model="llama3", temperature=0.0)
   ```

4. **Running an Interview:**
   ```python
   chain = prompt | model | output_parser
   response = chain.invoke({
       "level": "beginner",
       "categorization": "technical",
       "tone": "formal"
   })
   ```

## Best Practices

1. **Model Selection:**
   - Use GPT-4 for:
     - Advanced interview scenarios
     - Detailed feedback requirements
     - Complex role-playing situations
   - Use Ollama for:
     - Basic interview practice
     - Quick feedback sessions
     - Local deployment needs

2. **Parameter Configuration:**
   - Match level to candidate's experience
   - Align categorization with job requirements
   - Adjust tone based on industry/company culture

## Future Improvements

1. Add more specialized categories for different industries
2. Implement structured output parsing for better response handling
3. Add support for multi-turn conversations
4. Include industry-specific question banks
5. Develop metrics for evaluating interview performance

## Dependencies

- langchain
- langchain_openai
- langchain_ollama
- python-dotenv
- jupyter

## Resources

1. **LangChain Documentation**
   - [LangChain Official Documentation](https://python.langchain.com/docs/get_started/introduction)
   - [LangChain Prompt Templates Guide](https://python.langchain.com/docs/modules/model_io/prompts/prompt_templates/)
   - [LangChain Chat Models](https://python.langchain.com/docs/modules/model_io/models/chat/)
   - [LangChain Output Parsers](https://python.langchain.com/docs/modules/model_io/output_parsers/)

3. **Additional Learning**
   - [LangChain Cookbook](https://python.langchain.com/docs/additional_resources/tutorials)
   - [LangChain Templates](https://python.langchain.com/docs/templates)
   - [Best Practices for Prompt Engineering](https://python.langchain.com/docs/additional_resources/prompt_engineering)


# Perplexity.ai - First-Use Experience Review

## Overview
Perplexity.ai is an AI-powered search and response tool known for its efficiency and beginner-friendly approach. This document evaluates the onboarding experience, prompt interface, output clarity, and potential improvements.

## Questions & Responses

### 1. What was the onboarding or first-use experience like?
The first-use experience is highly engaging and smooth. The interface is intuitive, allowing users to explore its capabilities with minimal effort. The structured responses make interactions feel immediate and effective, creating an appetizing first impression.

### 2. Is the prompt interface beginner-friendly?
Yes, the prompt interface is designed for accessibility. Its clean layout ensures ease of use for both novices and experienced users. The system guides users naturally towards crafting queries without requiring extensive technical knowledge.

### 3. How clear and interactive are the outputs?
The responses are crisp, well-organized, and directly relevant to queries. Answers maintain a high level of clarity without unnecessary elaboration. While interactive refinement options could enhance engagement, the current output structure is highly effective for quick insights.

### 4. What improvements would you suggest? (Optional: include a mockup/sketch)
Here are some suggested enhancements to further improve usability:
- **Enhanced Interactivity:** Introducing adjustable response depth or follow-up suggestions could improve engagement.
- **Context Awareness:** Expanding the ability to retain deeper conversational context across queries would add more coherence.
- **UI Customization:** Offering themes or adjustable layout preferences could enhance user comfort.
- **Multimodal Inputs:** Incorporating voice or image-based queries would broaden accessibility.
- **Preview Pane:** A real-time response preview mechanism could refine user interactions.

## Conclusion
Perplexity.ai delivers an excellent first-use experience, with a beginner-friendly interface and highly precise outputs. Implementing refinements in interactivity and customization could further elevate user engagement.

---


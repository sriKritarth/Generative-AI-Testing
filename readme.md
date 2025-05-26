# Generative AI Testing Intern - Assignment

## PART 1: GenAI Model Testing Log

This document logs observations from testing two Large Language Models (LLMs): OpenAI `gpt-4o` and `deepseek-r1-distill-llama-70b`(inference proided by Groq). The tests were conducted using various prompts as demonstrated in the `PART1:GenAI Tool Testing & Observation Log\prompt_test.ipynb` notebook and evaluated on following performance parameter :

**Note:**
- **Accuracy:** Based on the factual correctness and relevance of the response to the prompt.
- **Latency/Performance Notes:** "to be determined" as direct measurement was not part of this observation.
- **Rating:** A subjective score reflecting overall quality, conciseness, and directness of the response.
- **Observed Bugs/Glitches:** The `<think>` tags in Groq's model output are noted as a characteristic rather than a bug, but they affect the usability of the raw output.


## PART 2: AI Interview Assistant Prompt Library

### Project Overview
An AI-powered interview assistant built with LangChain that leverages GPT-4 and Ollama's llama3 models to conduct adaptive mock interviews. The system offers flexible customization through three key parameters: experience level (beginner/advanced), skill category (technical/creative/analytical), and conversation tone (formal/casual/funny). Each interview follows a structured format with five essential components: introduction, self-introduction questions, follow-up questions, detailed feedback, and closing remarks. The assistant supports both cloud-based (GPT-4) and local (llama3) model deployments, providing flexibility in implementation and resource usage.

### Project Structure
PART2: Mini Prompt Library/
   ├── test.ipynb    # Main Jupyter notebook containing the implementation
   └── README.md     # This documentation file
   
### System Features

#### Interview Customization Parameters
The system accepts three main parameters to customize each interview session:
- **Level**: beginner or advanced
- **Categorization**: technical, creative, or analytical
- **Tone**: formal, casual, or funny

### Workflow

1. **Initialization**
   - Load selected language model (GPT-4 or llama3)
   - Set interview parameters (level, category, tone)
   - Initialize conversation history

2. **Interview Flow**
   - Generate personalized introduction
   - Present self-introduction questions
   - Process user responses
   - Generate relevant follow-up questions
   - Provide real-time feedback

3. **Feedback Generation**
   - Analyze response content and delivery
   - Evaluate technical accuracy
   - Assess communication style
   - Generate constructive feedback

4. **Session Management**
   - Track conversation progress
   - Maintain context awareness
   - Handle session transitions
   - Save interview summary

5. **Output Handling**
   - Format responses for readability
   - Generate session transcript
   - Provide actionable recommendations
   - Deliver closing remarks

   


## PART 3: Perplexity.ai Review

### Overview
A comprehensive evaluation of Perplexity.ai, an AI-powered search and response tool, focusing on its user experience, interface design, and output quality. The review analyzes the platform's strengths in accessibility and response clarity while identifying opportunities for enhanced interactivity and user engagement.

### Key Findings

1. **User Experience**
   - Intuitive and engaging first-use experience
   - Clean, accessible interface design
   - Immediate and effective response structure
   - Beginner-friendly interaction model

2. **Interface Design**
   - Streamlined prompt interface
   - Natural query guidance system
   - Minimal technical knowledge requirements
   - Clear, organized response format

3. **Output Quality**
   - Crisp and relevant responses
   - Well-structured information delivery
   - High clarity without unnecessary elaboration
   - Effective for quick insights

4. **Suggested Improvements**
   - Enhanced interactivity with adjustable response depth
   - Improved context retention across queries
   - Customizable UI themes and layouts
   - Support for multimodal inputs (voice/image)
   - Real-time response preview functionality

### Conclusion
Perplexity.ai demonstrates excellence in user experience and response quality, making it an effective tool for AI-powered search and information retrieval. While the platform already delivers strong performance, implementing the suggested improvements could further enhance its usability and engagement features.


## References Used in This Assignment

1. **LangChain Documentation**
   - [LangChain Official Documentation](https://python.langchain.com/docs/get_started/introduction)
   - [LangChain Prompt Templates Guide](https://python.langchain.com/docs/modules/model_io/prompts/prompt_templates/)
   - [LangChain Chat Models](https://python.langchain.com/docs/modules/model_io/models/chat/)
   - [LangChain Output Parsers](https://python.langchain.com/docs/modules/model_io/output_parsers/)

3. **Additional Learning**
   - [LangChain Cookbook](https://python.langchain.com/docs/additional_resources/tutorials)
   - [LangChain Templates](https://python.langchain.com/docs/templates)
   - [Best Practices for Prompt Engineering](https://python.langchain.com/docs/additional_resources/prompt_engineering)

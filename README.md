# RAG + Instruction Following Results from Python Wikipedia benchmark

The dataset is an artifact from an experiment conducted by [Arthur](https://arthur.ai/)

The code to reproduce our prompts and visualizations is available in the jupyter notebook

## Experiment

We wanted to compare how good LLMs are at answering questions using a context. Doing this task well involves an inverse skill: recognizing when the necessary information to answer a question is absent, and choosing instead to not answer. One name for this is “staying grounded” in the context that you provide in your prompt to the LLM.

If an LLM is perfectly grounded in its responses to our experiment, that means that the information it gives you can always be traced back to the context it was provided in its prompt (we provide the context we used across the board in our experiment, an excerpt from the Wikipedia page for Python, below).

Whether or not an LLM is not perfectly grounded in its response, we additionally check whether it was correct (either using our own background knowledge about the questions we were asking or performing some quick internet searching of our own). This way, we give credit to the models that have memorized lots of useful information in their training data, while also marking that they provided information that went outside of the scope of their provided context despite the instruction in the prompt not to do so.

## Questions + Context

The data consists of questions about the Python programming language. The context for each example is the summary paragraph & History section from the Python Wikipedia page.

The questions were chosen such that half of them are answerable given the context provided, and half of them are not answerable. We instruct the LLMs to only answer questions if they are answerable, i.e. if the necessary information is included in this context.

The context was chosen to be the opening paragraphs and the History section.

## Evaluation

While LLM-assisted evaluation is increasingly popular and time-saving, we decided it would be particularly valuable to grade answers manually, since doing so will help us measure the calibration of future LLM-assisted evaluators against our human judgment.

Each LLM answer was graded as either correct/incorrect. This was based on personal judgments based on whether the LLM was correctly understanding my questions and giving true information about the Python programming language. Most of the time this was perfectly straightforward and easy to do with my prior knowledge about Python, but occasionally I had to double check things myself with internet searches and carefully re-reading the Python wikipedia page myself to truly know whether the LLMs were saying true information or not.

Each LLM answer was also graded as either grounded/ungrounded. This was based on checking if the LLMs mentioned any bit of information that was not also mentioned in the provided context from Wikipedia. Therefore, mentioning true information about Python, e.g. its relation to C, would be graded as ungrounded if that information was not already included in the context we provided to the LLMs in our prompts.

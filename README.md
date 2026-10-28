# genai-agent-mutation-testing

# Using Gen AI to Automate Mutation Testing Across Microservices

In our project, we already had unit testing in place using JUnit and Mockito. We were also tracking code coverage, but one thing we wanted to improve was how effectively our tests were catching defects.

This is where I started exploring mutation testing.

I used Generative AI initially to understand mutation testing and how it could fit into our existing Java microservices. After going through a few examples and trying out the configurations, I was able to implement mutation testing in one of our microservices and integrate it into our Jenkins pipeline.

However, once we had it working, another challenge came up.

We had multiple microservices, and configuring mutation testing separately in each repository would involve repeating almost the same steps. Developers would need to understand the configuration, update the build files, make changes to Jenkins and verify that the reports were generated correctly.

I started thinking about whether we could use Gen AI to reduce this repetitive work.

## Building an AI Agent to Simplify the Setup

Instead of asking every team to configure mutation testing manually, we created an AI agent that could help developers introduce mutation testing into their microservices.

The idea was simple. A developer should be able to use the agent in an existing microservice repository, and the agent would help identify the required changes and prepare the configuration needed to enable mutation testing.

We provided the agent with instructions based on the implementation we had already completed.

These included understanding the existing project structure, identifying the build configuration, adding the required mutation testing setup and preparing the necessary Jenkins pipeline changes.

This helped us move away from explaining the same configuration steps to different teams.

Rather than starting from scratch, developers could use the agent to prepare the initial setup and then review the suggested changes before applying them.

One thing I found particularly useful was that we were not asking AI to design a completely new solution each time. We already had a working implementation, and the agent was helping us apply a similar approach across other microservices.

## Improving the Execution Time

While implementing mutation testing, we also noticed that running it against the entire repository could take considerable time.

This was not practical for every small code change, especially when mutation testing was part of the Jenkins pipeline.

I explored different configuration options and used Gen AI to understand how we could limit the scope of mutation testing.

We implemented an approach where mutation testing focused on the changed files instead of executing against the entire repository for every build.

This reduced unnecessary processing and made mutation testing more suitable for regular development.

We also added reporting so that developers could compare mutation testing results before and after their code changes.

The reports helped identify whether newly introduced or modified business logic was properly covered by meaningful unit tests.

The goal was not just to achieve a higher mutation score but to identify weaknesses in our test cases.

## How We Validated the AI-Generated Changes

One concern I had while building the agent was that different microservices might not have exactly the same configuration.

Even though most of our services followed a similar structure, there could still be differences in dependencies, plugins, project modules or Jenkins setup.

Because of this, we did not want developers to blindly accept whatever configuration the agent generated.

We used our existing working implementation as a reference and checked the changes suggested by the agent.

The important things to verify were whether the configuration was compatible with the microservice, whether the build completed successfully, whether mutation testing executed against the intended code and whether the reports were generated correctly.

We also needed to ensure that limiting mutation testing to changed files did not give developers the impression that the entire repository had been tested.

The agent helped with the repetitive configuration work, but developers remained responsible for reviewing and validating the changes.

## What Changed for the Team

The biggest benefit was that we made mutation testing easier to adopt across different microservices.

Previously, introducing mutation testing into another repository would have required developers to understand the setup and manually repeat the configuration steps.

With the AI agent, much of that initial work could be prepared automatically.

This allowed developers to spend more time reviewing the implementation and improving their unit tests rather than figuring out the same setup repeatedly.

The Jenkins integration also made mutation testing part of the development workflow, while the changed-file optimization helped keep execution time manageable.

For me, this was a useful example of applying Gen AI beyond asking questions or generating small pieces of code.

We used it to turn something we had learned and implemented once into a reusable approach that could help other teams.

## What I Learned

The main learning from this experience was that Gen AI becomes more useful when we give it a clear task, an existing working example and boundaries within which it should operate.

Initially, I was using AI mainly to understand mutation testing and explore configuration options.

Later, we used the same technology to build an agent that could help other developers perform similar configuration work.

I also realized that automation does not mean removing human review. Especially when making changes to build files and CI/CD pipelines, the generated output still needs to be checked.

If I were doing this again, I would define the validation checklist and supported project structures before extending the agent to more repositories.

Overall, this experience helped us introduce mutation testing into our development process and explore a more efficient way of adopting it across multiple microservices.

The most valuable part was not just learning mutation testing or building an AI agent. It was finding a way to reuse that learning so the wider team could benefit from it.

# Reflection And Documentation

This project serves as a space for reflection and documentation of my use of Windsurf for the Data & PreProcessing in Machine Learning Assignment

## Purpose

This repository is designed to capture thoughts, insights, and documentation related to the projects used this assignment

## Structure

This project is intentionally minimal to allow for flexible organization and growth as documentation needs evolve.

## Getting Started

This is a documentation repository - no special setup is required beyond having this directory available for storing and organizing reflective content.

## Windsurf Learning Log

- **How did you use Windsurf for each project?**
I used Windsurf as both a coding assistant and a project-structuring tool across all parts of the assignment. For the preprocessing project, I asked it to generate a full machine learning project layout—directories, modules, reusable pipelines, and notebooks—in the way an experienced ML engineer would structure their own work. Once the dataset was loaded, I used Windsurf to produce EDA visualisations, descriptive summaries, and a fully reusable preprocessing pipeline that handled feature engineering, missing-data treatment, scaling, and one-hot encoding in a clean, versionable way.

- For the train-test split experiments, Windsurf accelerated the workflow by generating synthetic datasets, plotting the effects of different split ratios, and helping me build walk-forward and temporal split routines. It allowed me to quickly test ideas that would normally take hours to code manually.

- Overall, I relied on Windsurf for rapid scaffolding, code generation, analysis, and iterative improvements—especially when I wanted to treat the work like a real production project with repeatable pipelines and CI/CD-ready components

- **What prompts or approaches were most effective?**
The most effective pattern was using detailed, explicit prompts combined with a strong persona. When I asked Windsurf to “act as an experienced ML engineer” and then requested a project structure or a specific implementation, the results were significantly better—more idiomatic, more realistic, and closer to industry standards.

- Another high-leverage prompt style was to specify exactly what objects or files I wanted produced (e.g., a preprocessing module, a synthetic dataset generator, a plotting function, or a set of model comparison routines). Windsurf responds well when the scope is clear and when each step builds on the previous one.

- **What did Windsurf struggle with, and how did you address it?**
Windsurf occasionally produced errors, especially when paired with high-reasoning private LLMs such as GPT-5.1. These models sometimes attempted to “over-reason” simple tasks, which resulted in partial outputs or timeouts. To address this, I switched to lower-reasoning or more stable models like GPT-4 or SWE-1.5, which handled execution and iterative editing more reliably.

- There were also issues accessing the Hugging Face dataset API from within Windsurf’s environment. To work around that, I guided Windsurf to use alternative dataset-loading strategies (manual downloads, direct parquet reads, or simplified URLs).

- When errors surfaced in multi-file codebases, Windsurf sometimes needed very explicit guidance about which file to inspect. Giving it the full stack trace and a pointer to the suspected file usually resolved this


- **How did using Windsurf change your learning process?**
Windsurf dramatically accelerated my learning because it removed the friction of setup and boilerplate. I could move straight into analysis, modelling, and experimentation. For example, being able to generate synthetic datasets quickly allowed me to test the effects of different train-test splits on model performance without waiting for real-world datasets to download or preprocess.

- It also changed how I approached debugging. Instead of spending long hours manually tracing errors, I could pass Windsurf the entire stack trace and have it locate the root cause, explain why it happened, and propose a fix. It became a collaborative learning loop: write code, run it, inspect the result, ask Windsurf for a breakdown, then push the analysis further.

- Windsurf didn’t just save time—it made it easier to think like an ML engineer by exposing me to patterns, structures, and workflows I can now replicate independently.

## Key Takeaways

- **What was the most surprising thing you learned?**
The most surprising discovery was how effectively Windsurf handled complex, multi-file debugging tasks. I could feed it an entire stack trace, and it would not only identify the exact source of the error but also explain why it occurred, describe the implications of the bug, and propose a precise fix. After I approved the suggestion, it would automatically apply the correction directly to the codebase.

- For me, this demonstrated how far AI-assisted engineering has come. Windsurf wasn’t just autocompleting code—it was operating as a reasoning engine capable of analysing my entire project, maintaining context across files, and guiding me through high-level ML engineering decisions

- **What preprocessing technique do you think you'll use most?**
The preprocessing technique I will use the most is EDA with targeted visualisation, especially the workflow where I ask Windsurf to analyse the dataset directly against the target variable. This became the biggest timesaver in the entire project. With a single prompt, Windsurf produced a full breakdown of the dataset—identifying categorical, numeric, boolean, and date-based features; showing how each feature was distributed; and highlighting how those distributions related to the target. It also surfaced the count and pattern of missing values immediately, which helped me decide early on whether I should impute, drop, or engineer around them.

- This type of targeted EDA gives a level of clarity that normally takes a long time to build manually, and it sets the foundation for every subsequent preprocessing choice: encoding, scaling, imputation, and feature selection. Because of how quickly it gives me an accurate mental model of the dataset, I expect this will remain my most-used preprocessing step in future machine learning projects

- **What would you do differently in a real-world project?**
In a real-world setting, I would start by building a proper data pipeline that supplies fresh data on a schedule rather than manually loading static files. I would also make sure the dataset is as close to raw as possible, because raw data gives you far more room to engineer meaningful features and improve model accuracy.

- Instead of keeping most of the logic inside notebooks, I would refactor everything into modular, reusable Python scripts—separating ingestion, preprocessing, feature engineering, training, evaluation, and inference. From there, I would set up a GitHub Actions or Azure Pipeline workflow to automate the entire process: ingest the latest dataset from the data pipeline, run the preprocessing and model training pipeline, register the trained model as an artifact, and then use that artifact to generate predictions.

- Essentially, I would move from a notebook-driven workflow to a production-ready MLOps pipeline that is automated, maintainable, testable, and capable of handling continuous data updates

- **One question or topic you want to explore further**
I want to explore how to build a fully reproducible, end-to-end machine learning pipeline—one that can take raw data, preprocess it consistently, train a model, register the resulting artifact, and deploy it automatically for real-time or scheduled predictions. I’ve built parts of this during the project, but I want to go deeper into the operational side: versioning data, tracking experiments, automating retraining, and managing deployed models in a way that is stable and production-ready. Understanding how to design this kind of pipeline would not only strengthen my MLOps skills but also make my future projects easier to maintain, scale, and monitor
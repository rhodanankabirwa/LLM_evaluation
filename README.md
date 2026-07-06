# LLM Ensembel Evaluation
This repository contains a preliminary evaluation of Large Language Model (LLM) ensemble methods for domain specific question answering. The goal is to examine whether ensemble approaches generate quantitatively better responses than individual candidate LLMs or single general purpose LLMs.

## Ensemble methods
The study adapts two ensemble approaches
1. LLM Blender
Source: https://github.com/yuchenlin/LLM-Blender
LLM Blender ranks candidate outputs from multiple LLMs. In this experiment, we adapted its ranking anf fusion approaches to evaluate whether combined outputs improve output quality.

2. PackLLM
Source: https://github.com/cmavro/PackLLM
PackLLM leverages multing LLMs using and ensemble-style framework. In this experiement, we used PackLLM as a second ensemble baseline for comparison.

The scripts for both ensembles used in this experiment were developed to support prompt-specific experimentation, flexible model selection, readable output saving, and SLURM-based testing. These changes were made for usability and deployment, not to alter the core ensemble algorithms.

## Research Objective
The overall aim of this study was to assess the robustness of the responses from LLM ensembles to simple and complex queries and to identify any gaps in the use of
the ensemble approach.

## Evaluation domains
The preliminary evaluation is based on questions from:
Polar science
Agriculture and soil management

## Implementation Notes

The ensemble methods were run separately using the code from their respective GitHub repositories. The core inference logic from the original implementations was preserved as much as possible. This project did not aim to redesign or optimize the ensemble algorithms themselves.

However, the original LLM-Blender and PackLLM scripts were not optimized for user-driven, prompt-specific inference in this experimental setting. Therefore, dedicated scripts were developed for each setup. These scripts introduced practical modifications needed for running controlled prompt-level experiments while preserving the original ensemble behavior.

The main modifications were:

- **Prompt-level input flexibility:** prompts can be passed dynamically as command-line arguments rather than being fixed inside the script.
- **Flexible model selection:** candidate models can be selected or changed more easily for different experimental runs.
- **Input-output handling:** model outputs and ensemble responses are saved in readable plain-text result files.
- **Deployment efficiency:** the scripts support iterative testing on a SLURM-based computing environment.

For the polar science question, domain experts ranked the responses based on the quality of the output. The Agricltural question answer output was not formally evaluated by a domain expert and as such, the observations are treated preliminarily.

## Data and results
The raw outputs are provided in the directory.
 
llm_blender_polar_domain_candidate_responses.csv | Candidate model responses for the Antarctic sea ice and ice shelf question.

llm_blender_agriculture_domain_candidate_responses.csv | Candidate model responses for the Agriculture and Soil Management question.

Final_model_generated_responses.csv | Final responses from ChatGPT, PackLLM and LLM-Blender.

## Preliminary Findings
In the polar science example, the single LLM responses was ranked highest by the domain expert, followed by PackLLM and then LLM Blender. On the other hand, the ensemble generated responses by PackLLM contained ungrounded claims for the agricultural query.

## Limitations
This work is a small preliminary evaluation. The results are based on a single prompt in each of the two domains. Additional evaluation is critical before drawing broad conclusions.

## Citation

If using the ensemble methods, please cite or refer to their original repositories:

- LLM-Blender: https://github.com/yuchenlin/LLM-Blender
- PackLLM: https://github.com/cmavro/PackLLM


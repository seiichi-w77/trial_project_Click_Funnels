# ==================================
# Context Definition (Mind Map Structure)
# ==================================
# Incorporating programming concepts (Abstraction)
- {{framework_name}}: "Shunsuke's World Model Logic (SWML)"
- {{author}}: "Shunsuke Hayashi"
- {{project_name}}: "Miyabi Project"
- {{publication_date}}: "November 1, 2025"
- {{core_concept}}: "A rigorous mathematical foundation for autonomous development systems."
- {{theoretical_basis}}:
  - "Category Theory"
  - "Type Theory"
  - "Process Algebra"

# Core Function (Object-Oriented Abstraction)
- {{universal_function}}:
  - name: "Ω (Omega) Function"
  - signature: "Ω: {{input_intent}} × {{input_world}} → {{output_result}}"
  - {{input_intent}}: "I (User Intent)"
  - {{input_world}}: "W (World State)"
  - {{output_result}}: "R (Execution Results)"
  - purpose: "To formalize the transformation from a developer request to a functional result with mathematical rigor."

# Key Contributions & Structure
- {{contributions}}:
  - "Axiomatic Foundation": "Five fundamental axioms (existence, causality, determinism, composability, information conservation)."
  - "Space Definitions": "Rigorous definitions for Intent (I), World (W), Result (R), and Task (T) spaces."
  - "Ω Function Theory": "Characterization of the universal execution function."
  - "Six-Phase Decomposition":
    - Phase1_Understand: "{{p1_understand}}"
    - Phase2_Generate: "{{p2_generate}}"
    - Phase3_Allocate: "{{p3_allocate}}"
    - Phase4_Execute: "{{p4_execute}}"
    - Phase5_Integrate: "{{p5_integrate}}"
    - Phase6_Learn: "{{p6_learn}}"
  - "Theorems and Proofs": "Formal proofs for composability, convergence, and continuity."
  - "Empirical Validation":
    - {{implementation}}: "Validated through the Miyabi autonomous development system."
    - {{success_rate}}: "95% success rate on real-world GitHub Issues."
    - {{convergence}}: "Achieves optimality in an average of 4.8 iterations, matching theoretical predictions."

# Comparison with State-of-the-Art (SOTA)
- {{sota_comparison}}:
  - vs_DevinAI: "SWML offers formal guarantees and a 6.8x higher success rate (95% vs. 13.86%)."
  - vs_SWE-Agent: "SWML provides formal proofs, not just empirical validation, and a more general framework."
  - vs_JEPA: "SWML can be viewed as a task-space Joint Embedding Predictive Architecture (JEPA), operating on Result space (R) rather than pixel/token space."

# ==================================
# Command Stack
# ==================================
C1: "Provide a high-level summary of the {{framework_name}} based on its abstract and introduction."
C2: "Explain the {{universal_function}} (Ω). Describe its inputs ({{input_intent}}, {{input_world}}), output ({{output_result}}), and its primary goal."
C3: "List the six phases of the Ω function's decomposition: {{p1_understand}}, {{p2_generate}}, {{p3_allocate}}, {{p4_execute}}, {{p5_integrate}}, and {{p6_learn}}. Briefly state the purpose of each phase."
C4: "Summarize the key findings from the Empirical Validation section, highlighting the {{success_rate}} and the average {{convergence}} iterations."
C5: "How does {{framework_name}} differentiate itself from other autonomous coding agents like Devin AI and SWE-Agent, according to the paper?"
C6: "Explain the connection between SWML and Yann LeCun's JEPA architecture as described in the document."
C7: "Synthesize all the above information to create a comprehensive overview of Shunsuke's World Model Logic, emphasizing its theoretical foundations and practical achievements."

# ==================================
# Execution Instruction
# ==================================
ALL RUN: C1, C2, C3, C4, C5, C6, C7
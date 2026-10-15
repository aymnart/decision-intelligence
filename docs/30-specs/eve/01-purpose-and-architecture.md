> Part of [Eve Implementation Specification](README.md).

# Purpose

This document defines how to implement the Decision Intelligence Engine using Vercel Eve.

Eve is used as the agent execution runtime.

The core intelligence must remain independent from Eve.

Eve provides:

- agent orchestration
- subagents
- tools
- skills
- durable workflows
- human approvals
- long-running execution
- state management

The Decision Intelligence Engine remains the core product.

---

# Official Eve Resources

Before implementation, study:

- Eve Documentation:
<https://eve.dev/llms.txt>

- Eve Subagents:
<https://vercel.com/kb/guide/how-to-use-eve-subagents>

- Eve Knowledge Base:
<https://vercel.com/kb/eve>

---

# Core Architecture

The relationship between Eve and the Dynamic Council Assembly Engine:

```
                 User Request

                      |

                      v

        Decision Intelligence Engine

                      |

                      v

              Intent Analyzer

                      |

                      v

              Domain Detection

                      |

                      v

           Council Assembly Engine

                      |

        +-------------+-------------+

        |                           |

        v                           v

 Required Experts            Permanent Experts

 (domain knowledge base)     (quality control)

        |                           |

        +-------------+-------------+

                      |

                      v

         Expert runners (Eve workers)

                      |

                      v

             Debate + Consensus

                      |

                      v

             Decision + Memory

                      |

                      v

             Execution Workflow

                      |

                      v

                  Artifacts
```

MVP: Eve may execute built-in expert roles as workers.

Post-MVP: users can connect custom Eve agents as `type: "eve-agent"` council members through the same `CouncilExpert` interface.

---

# Important Rule

Eve agents are NOT the council.

They are workers executing expert roles selected by the Council Assembly Engine.

The council logic belongs in the application layer.

Future custom Eve agents must still implement:

```
CouncilExpert {
  type: "eve-agent"
  analyze(context): ExpertOpinion
}
```

Example future connection:

```
My Agent

↓

Eve Runtime

↓

Council Expert Interface
```

Company examples:

```
Internal Security Agent

Internal Finance Agent

Company Historian Agent
```

Do not build custom Eve-agent council members before MVP validates autonomous assembly.

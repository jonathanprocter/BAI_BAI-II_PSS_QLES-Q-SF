# Mental Health Assessment Web Application - Development Prompt

## Project Overview
Create a comprehensive, client-side mental health assessment web application that integrates four validated psychological assessment tools (BAI, BDI-II, PSS, QLES-Q-SF) with real-time scoring, factor analysis, and personalized actionable insights.

## Core Requirements

### 1. Assessment Integration
Implement the following questionnaires with exact scoring algorithms:

#### Beck Anxiety Inventory (BAI)
- 21 items, 4-point scale (0-3)
- Scoring ranges: 0-21 (low), 22-35 (moderate), 36+ (high)
- Factor domains to analyze:
  - Somatic symptoms (items 1-3, 6-8, 11-13, 18-21)
  - Subjective anxiety (items 4-5, 9-10, 14-17)
  - Panic-related symptoms (items 7, 11, 12, 15, 16)
  - Autonomic symptoms (items 2, 18, 19, 20, 21)

#### Beck Depression Inventory-II (BDI-II)
- 21 items, 4-point scale (0-3)
- Scoring ranges: 0-13 (minimal), 14-19 (mild), 20-28 (moderate), 29-63 (severe)
- Factor domains to analyze:
  - Cognitive symptoms (items 1-3, 5-9, 14)
  - Affective symptoms (items 4, 10, 11, 12, 13)
  - Somatic symptoms (items 15-21)

#### Perceived Stress Scale (PSS-10)
- 10 items, 5-point scale (0-4)
- Reverse score items 4, 5, 7, 8
- Scoring ranges: 0-13 (low), 14-26 (moderate), 27-40 (high)
- Factor domains:
  - Perceived helplessness (items 1, 2, 3, 6, 9, 10)
  - Perceived self-efficacy (items 4, 5, 7, 8)

#### Quality of Life Enjoyment and Satisfaction Questionnaire - Short Form (Q-LES-Q-SF)
- 16 items, 5-point scale (1-5)
- Calculate percentage of maximum possible score
- Factor domains:
  - Physical well-being (items 1, 12, 13)
  - Emotional well-being (items 2, 14)
  - Social functioning (items 5, 6)
  - Occupational functioning (items 3, 4)
  - Daily activities (items 7, 8)
  - Overall satisfaction (items 14, 16)

### 2. Technical Specifications

#### Frontend Architecture
```javascript
// Core components structure
- AssessmentContainer
  - QuestionnaireSelector
  - QuestionRenderer
  - ProgressIndicator
  - ResponseValidator
- AnalysisEngine
  - ScoreCalculator
  - FactorAnalyzer
  - TrendIdentifier
  - InsightGenerator
- ReportGenerator
  - IndividualReports
  - IntegratedNarrative
  - ActionPlanBuilder
  - ExportManager
```

#### Data Structure
```javascript
{
  sessionId: "uuid",
  timestamp: "ISO-8601",
  assessments: {
    BAI: { responses: [], score: null, factors: {} },
    BDI: { responses: [], score: null, factors: {} },
    PSS: { responses: [], score: null, factors: {} },
    QLES: { responses: [], score: null, factors: {} }
  },
  analysis: {
    patterns: [],
    riskFactors: [],
    protectiveFactors: [],
    recommendations: []
  }
}
```

### 3. Client-Side Processing Requirements

#### Real-time Scoring
- Calculate scores immediately upon completion of each assessment
- Display visual feedback (progress bars, gauges, charts)
- No server communication required for scoring

#### Factor Analysis Implementation
```javascript
// Example factor calculation for BAI
calculateBAIFactors(responses) {
  return {
    somatic: calculateMean(responses, [0,1,2,5,6,7,10,11,12,17,18,19,20]),
    subjective: calculateMean(responses, [3,4,8,9,13,14,15,16]),
    panic: calculateMean(responses, [6,10,11,14,15]),
    autonomic: calculateMean(responses, [1,17,18,19,20])
  };
}
```

### 4. Comprehensive Report Generation

#### Individual Assessment Reports
Each assessment should generate:
- Total score with interpretation
- Factor breakdown with subscale scores
- Percentile rankings (based on normative data)
- Item-level analysis highlighting extreme responses
- Visual representations (radar charts, bar graphs)

#### Integrated Assessment Narrative
Generate a cohesive narrative that:
- Identifies cross-assessment patterns
- Highlights convergent findings
- Notes divergent or contradictory results
- Provides context for score interpretation
- Uses person-first, strength-based language

### 5. Actionable Insights Framework (ACT/Narrative/DBT/Existential Integration)

#### Pattern Recognition with Therapeutic Lens
```javascript
identifyPatterns() {
  // Cross-reference using ACT/DBT/Narrative frameworks
  return {
    primaryPattern: "description",
    therapeuticFramework: {
      ACT: {
        fusedThoughts: [], // Cognitive fusion patterns
        avoidanceBehaviors: [], // Experiential avoidance
        valuesDiscrepancy: [], // Life not aligned with values
        psychologicalInflexibility: []
      },
      Narrative: {
        problemStory: "", // Dominant problem narrative
        uniqueOutcomes: [], // Exceptions to problem story
        externalizedProblems: [] // Problems as separate from person
      },
      DBT: {
        emotionDysregulation: [],
        interpersonalChallenges: [],
        distressIntolerance: [],
        mindfulnessDeficits: []
      },
      Existential: {
        meaningCrisis: [],
        freedomAnxiety: [],
        isolationThemes: [],
        mortalityConcerns: []
      }
    },
    severity: "mild|moderate|severe",
    interventionPriority: 1-5
  };
}
```

#### ACT-Informed Recommendations
```javascript
generateACTInterventions(patterns) {
  return {
    valuesExploration: {
      prompt: "What matters most deeply to you?",
      exercises: [
        "Values card sort",
        "Eulogy exercise",
        "Sweet spot analysis (values + strengths + passion)"
      ]
    },
    defusion: {
      techniques: [
        "Thank your mind practice",
        "Leaves on a stream meditation",
        "Naming the story ('The I'm not good enough story')"
      ]
    },
    acceptance: {
      practices: [
        "Make room for difficult emotions",
        "Expansion technique for physical sensations",
        "Self-compassion break"
      ]
    },
    committedAction: {
      steps: "Small values-based actions despite discomfort"
    }
  };
}
```

#### Narrative Therapy Reframing
```javascript
generateNarrativeInterventions(patterns) {
  return {
    externalization: {
      language: "The Anxiety" instead of "My anxiety",
      questions: [
        "When did The Anxiety first enter your life?",
        "What does The Anxiety want for you?",
        "When have you resisted The Anxiety's influence?"
      ]
    },
    uniqueOutcomes: {
      exploration: "Times when the problem had less influence",
      strengthSpotting: "Hidden stories of resilience"
    },
    reAuthoring: {
      preferredStory: "Who you are becoming",
      intentionalState: "Your values in action"
    }
  };
}
```

#### DBT Skills Integration
```javascript
generateDBTInterventions(patterns) {
  return {
    distressTolerance: {
      TIPP: "Temperature, Intense exercise, Paced breathing, Paired muscle relaxation",
      ACCEPTS: "Activities, Contributing, Comparisons, Emotions, Push away, Thoughts, Sensations",
      selfSoothe: "5 senses grounding"
    },
    emotionRegulation: {
      PLEASE: "treat PhysicaL illness, balance Eating, avoid mood-Altering substances, balance Sleep, get Exercise",
      oppositeAction: "Act opposite to emotion urge",
      checkTheFacts: "Is my emotion justified?"
    },
    interpersonalEffectiveness: {
      DEARMAN: "Describe, Express, Assert, Reinforce, Mindful, Appear confident, Negotiate",
      GIVE: "Gentle, Interested, Validate, Easy manner",
      FAST: "Fair, Apologies (no excessive), Stick to values, Truthful"
    },
    mindfulness: {
      what: "Observe, Describe, Participate",
      how: "Non-judgmentally, One-mindfully, Effectively"
    }
  };
}
```

#### Existential Themes Explorer
```javascript
generateExistentialInsights(patterns) {
  return {
    meaning: {
      questions: [
        "What gives your suffering meaning?",
        "How does this challenge connect to your life purpose?",
        "What legacy do you want to create from this experience?"
      ],
      practices: ["Logotherapy exercises", "Meaning-making journaling"]
    },
    freedom: {
      responsibility: "Choosing your response to unchangeable situations",
      authenticity: "Living according to your truth, not others' expectations"
    },
    connection: {
      isolation: "Shared human experience of suffering",
      belonging: "Finding your tribe who understands"
    },
    finitude: {
      mortality: "How does limited time clarify priorities?",
      impermanence: "This too shall pass - both joy and suffering"
    }
  };
}

### 6. Export Functionality with Therapeutic Framework

#### Export Formats
- **PDF Report**: Comprehensive formatted document with therapeutic approach sections
- **CSV Data**: Raw scores and responses
- **JSON**: Complete session data including therapeutic insights
- **Clinical Summary**: One-page provider-ready format with ACT/DBT/Narrative/Existential conceptualization
- **Personal Workbook**: Interactive exercises based on identified patterns

#### Export Content Structure
```javascript
{
  metadata: {
    generatedDate: "",
    assessmentsCompleted: [],
    totalDuration: "",
    therapeuticFrameworks: ["ACT", "Narrative", "DBT", "Existential"]
  },
  scores: {
    // All assessment scores and subscales
  },
  therapeuticConceptualization: {
    ACT: {
      psychologicalFlexibility: {},
      valuesAssessment: {},
      fusionPatterns: [],
      avoidancePatterns: []
    },
    Narrative: {
      problemStory: "",
      uniqueOutcomes: [],
      preferredIdentity: "",
      externalizedProblems: []
    },
    DBT: {
      skillsDeficits: {},
      dysregulationPatterns: [],
      strengthAreas: []
    },
    Existential: {
      primaryThemes: [],
      meaningStructures: {},
      authenticityGaps: []
    }
  },
  narrative: {
    integrated: "", // Woven story using all approaches
    strengthBased: "", // Focus on resilience and resources
    clinical: "" // For providers familiar with these modalities
  },
  recommendations: {
    ACTInterventions: {
      immediate: [],
      weeklyPractices: [],
      monthlyGoals: []
    },
    DBTSkills: {
      distressTolerance: [],
      emotionRegulation: [],
      interpersonalEffectiveness: [],
      mindfulness: []
    },
    NarrativeExercises: {
      externalization: [],
      reAuthoring: [],
      witnessing: []
    },
    ExistentialExplorations: {
      meaningMaking: [],
      freedomExercises: [],
      connectionPractices: []
    }
  },
  resources: {
    crisisLines: {
      national: [],
      local: [],
      text: [],
      warmLines: [] // Non-crisis support
    },
    therapeuticResources: {
      ACT: ["Books", "Apps", "Worksheets", "Videos"],
      DBT: ["Skills apps", "Workbooks", "Groups"],
      Narrative: ["Questions", "Letters", "Ceremonies"],
      Existential: ["Readings", "Meditations", "Discussions"]
    },
    localProviders: {
      ACTTherapists: [],
      DBTPrograms: [],
      NarrativeTherapists: [],
      ExistentialTherapists: []
    }
  },
  personalWorkbook: {
    valuesWorksheets: [],
    DBTDiaryCards: [],
    narrativePrompts: [],
    existentialReflections: []
  }
}
```

### 7. Therapeutic Language Engine

#### Language Patterns by Framework
```javascript
const therapeuticLanguage = {
  ACT: {
    patterns: [
      "making room for", // vs "getting rid of"
      "thoughts and feelings" // vs "symptoms"
      "workable" // vs "good/bad"
      "toward/away moves" // values direction
      "psychological flexibility"
    ],
    metaphors: [
      "Passengers on the bus",
      "Tug of war with monster",
      "Quicksand",
      "Weather patterns of the mind"
    ]
  },
  Narrative: {
    patterns: [
      "The [Problem Name]" // externalization
      "times when", // unique outcomes
      "preferred story",
      "influence of/on the problem",
      "sparkling moments"
    ],
    questions: [
      "How did you resist?",
      "Who would be least surprised?",
      "What does this say about you?"
    ]
  },
  DBT: {
    patterns: [
      "wise mind",
      "dialectical" // both/and thinking
      "effective" // vs right/wrong
      "skillful",
      "vulnerability factors"
    ],
    acronyms: [
      "PLEASE", "TIPP", "STOP",
      "DEARMAN", "GIVE", "FAST"
    ]
  },
  Existential: {
    patterns: [
      "meaning-making",
      "authentic existence",
      "freedom and responsibility",
      "being-with",
      "thrownness"
    ],
    themes: [
      "What makes life worth living?",
      "How do I choose myself?",
      "What is my relationship with uncertainty?"
    ]
  }
};
```

### 8. Nuanced Intervention Generator

```javascript
class TherapeuticInterventionGenerator {
  generatePersonalizedInterventions(assessmentData, patterns) {
    const interventions = {
      immediate: this.generateCrisisInterventions(assessmentData),
      weekly: this.generateWeeklyPractices(patterns),
      monthly: this.generateMonthlyGoals(patterns),
      ongoing: this.generateMaintenancePractices(patterns)
    };
    
    // Ensure interventions are specific, not generic
    return this.personalizeInterventions(interventions, assessmentData);
  }
  
  personalizeInterventions(interventions, data) {
    // Match interventions to specific symptoms and patterns
    // Example: If high BAI somatic + low QLES energy
    if (data.BAI.factors.somatic > 2 && data.QLES.items[0] < 3) {
      interventions.immediate.push({
        framework: "DBT",
        skill: "TIPP",
        rationale: "Your body is holding anxiety. Temperature change can reset your nervous system.",
        specific: "Keep ice packs ready. When chest tightens, apply to face for 30 seconds."
      });
      
      interventions.weekly.push({
        framework: "ACT",
        practice: "Body scan with acceptance",
        rationale: "Making friends with physical sensations rather than fighting them.",
        specific: "Daily 10-min scan, saying 'hello' to tight areas without trying to relax them."
      });
    }
    
    // Ensure cultural sensitivity and personal relevance
    return this.culturallyAdapt(interventions);
  }
  
  culturallyAdapt(interventions) {
    // Add options for different cultural contexts
    interventions.forEach(int => {
      int.alternatives = this.generateCulturalAlternatives(int);
    });
    return interventions;
  }
}
```

### 9. Integration Across Modalities

```javascript
class ModalityIntegrator {
  weaveTherapeuticNarrative(data) {
    const narrative = {
      opening: this.createStrengthBasedOpening(data),
      
      // ACT thread
      valuesExploration: this.exploreValuesGap(data),
      flexibilityAssessment: this.assessPsychologicalFlexibility(data),
      
      // Narrative thread  
      problemExternalization: this.externalizeProblems(data),
      uniqueOutcomes: this.identifyExceptions(data),
      
      // DBT thread
      skillsAssessment: this.evaluateDBTSkills(data),
      dysregulationPatterns: this.identifyPatterns(data),
      
      // Existential thread
      meaningExploration: this.exploreMeaning(data),
      authenticityGaps: this.assessAuthenticity(data),
      
      // Integrated recommendations
      synthesis: this.synthesizeApproaches(data),
      actionPlan: this.createIntegratedPlan(data)
    };
    
    return this.formatAsCoherentNarrative(narrative);
  }
  
  synthesizeApproaches(data) {
    // Find where approaches complement each other
    // Example: DBT distress tolerance + ACT acceptance + Existential meaning
    return {
      synergies: [
        "DBT's distress tolerance provides immediate relief while ACT's acceptance creates long-term flexibility",
        "Narrative externalization supports ACT defusion techniques",
        "Existential meaning-making deepens ACT values work",
        "DBT interpersonal skills enhance Narrative's audience recruitment"
      ],
      integratedPractices: this.createHybridInterventions(data)
    };
  }
  
  createHybridInterventions(data) {
    // Combine approaches for powerful interventions
    return [
      {
        name: "Values-Based Distress Tolerance",
        combines: ["ACT values", "DBT TIPP"],
        practice: "When distressed, connect to WHY you're willing to feel this (values) while using TIPP"
      },
      {
        name: "Existential Exposure",
        combines: ["Existential meaning", "ACT willingness"],
        practice: "Sit with uncertainty about life's meaning while taking valued action anyway"
      },
      {
        name: "Re-authoring with Wise Mind",
        combines: ["Narrative re-authoring", "DBT wise mind"],
        practice: "Access wise mind to identify moments you've lived your preferred story"
      }
    ];
  }
}

### 7. UI/UX Requirements

#### Design Principles
- Mobile-first responsive design
- WCAG 2.1 AA accessibility compliance
- Dark mode support
- Auto-save functionality
- Session recovery capability

#### User Flow
1. **Welcome Screen**: Brief introduction, consent, estimated time
2. **Assessment Selection**: Choose individual or complete battery
3. **Question Presentation**: One question per screen, progress indicator
4. **Immediate Feedback**: Score display with initial interpretation
5. **Comprehensive Results**: Interactive dashboard with all results
6. **Action Planning**: Guided recommendation selection
7. **Export Options**: Multiple format choices with preview

### 8. Advanced Features

#### Longitudinal Tracking
- Store multiple sessions locally (IndexedDB)
- Compare results over time
- Identify improvement/deterioration trends
- Generate progress reports

#### Risk Detection Algorithm
```javascript
assessRisk() {
  const flags = [];
  
  // Suicide risk (BDI item 9)
  if (BDI.item9 >= 1) flags.push({
    type: "suicide_ideation",
    severity: BDI.item9,
    action: "immediate_resources"
  });
  
  // Severe anxiety
  if (BAI.total >= 36) flags.push({
    type: "severe_anxiety",
    action: "professional_consultation"
  });
  
  return flags;
}
```

### 9. Validation & Quality Assurance

#### Input Validation
- Ensure all questions answered
- Detect response patterns (straight-lining)
- Flag inconsistent responses
- Time-based validity checks

#### Clinical Safeguards
- Crisis resource display for high-risk scores
- Disclaimer about not replacing professional assessment
- Encourage professional consultation when indicated
- Provide emergency contact information

### 10. Example Integrated Narrative Output (ACT/Narrative/DBT/Existential Approach)

```markdown
## Comprehensive Assessment Summary: Your Story of Resilience and Growth

Based on your responses across all four assessments, we can explore the landscape of your current experience through multiple therapeutic lenses, each offering unique pathways toward psychological flexibility and well-being.

### The Current Chapter of Your Story

Your assessment reveals that "The Anxiety" (BAI: 28) and "The Overwhelm" (PSS: 24) have been significant characters in your recent life story. These uninvited guests appear to be working together, particularly affecting your body through tension, sleep disruption, and fatigue. Rather than seeing these as flaws or failures, we can understand them as your system's attempt to protect you from perceived threats - even when those protective strategies may no longer serve you.

### Values and Life Direction (ACT Perspective)

The gap between your current experience and your quality of life satisfaction suggests a disconnection from what matters most to you. Your preserved family relationships (QLES: 4/5) hint at core values around connection and love that remain strong anchors. The moderate depression symptoms (BDI-II: 16) may reflect the cost of fighting against difficult emotions rather than making room for them while still moving toward what you value.

**Psychological Flexibility Assessment:**
- Experiential Avoidance: High (avoiding anxiety-provoking situations)
- Cognitive Fusion: Moderate (getting caught in worry thoughts)
- Values Clarity: Emerging (family connections remain clear)
- Committed Action: Reduced (energy depletion affecting action)

### Your Unique Outcomes (Narrative Therapy Lens)

Despite The Anxiety's influence, you've maintained confidence in handling personal problems (PSS item 4) - this is a powerful counter-story to the dominant narrative of being overwhelmed. These moments when you've stood up to The Anxiety deserve recognition and exploration. What knowledge and skills have you used in these victories that The Anxiety wants you to forget?

### Skills and Dysregulation Patterns (DBT Framework)

**Current Skill Deficits and Strengths:**
- Distress Tolerance: LOW - Physical symptoms suggest difficulty "riding the wave"
- Emotion Regulation: MODERATE - Some capacity remains but energy-depleted
- Interpersonal Effectiveness: STRONG - Relationships remain satisfying
- Mindfulness: VARIABLE - Present-moment awareness hijacked by future worries

### Existential Themes Present

Your experience touches on fundamental human concerns:
- **Meaning**: "What is the purpose of this suffering?"
- **Freedom**: Feeling trapped by circumstances vs. choosing your response
- **Isolation**: Though connected to family, existential aloneness in your struggle
- **Finitude**: Anxiety about time passing without living fully

### Your Personalized Path Forward

**Week 1: Foundation Building**

*ACT Focus - Making Room*
- Practice "Dropping Anchor" (3x daily, 3 minutes): 
  - Acknowledge thoughts/feelings ("Here's anxiety")
  - Connect with your body (press feet into floor)
  - Engage with the world (notice 5 things you see)
- Values Clarification: Complete "What I Want My Life to Stand For" worksheet

*DBT Skills - Immediate Stabilization*
- TIPP for intense anxiety moments:
  - Temperature: Cold water on face
  - Intense exercise: 1-minute jumping jacks
  - Paced breathing: 4-7-8 technique
  - Paired muscle relaxation: Tense and release
- Daily PLEASE checklist for emotion vulnerability

*Narrative Practice - Externalization*
- Name your anxiety/stress (e.g., "The Storm," "The Critic")
- Daily journal prompt: "Today I noticed The [Name] trying to convince me that..."
- "However, I also noticed that I..."

**Weeks 2-4: Building Psychological Flexibility**

*ACT Interventions*
- Defusion Practice: "I'm having the thought that..." prefix
- Values-Based Action Planning:
  - Identify one small daily action aligned with family connection
  - One weekly action toward neglected value area
- Acceptance Meditation: "Leaves on a Stream" (10 min daily)

*DBT Skills Training*
- Emotion Regulation:
  - Check the Facts worksheet for anxious predictions
  - Opposite Action when anxiety says "avoid"
  - Self-Soothe kit creation (5 senses)
- Interpersonal Effectiveness:
  - Use GIVE skills to maintain family connections
  - Practice FAST for self-respect in overwhelming situations

*Narrative Re-authoring*
- Weekly reflection: "Times I've influenced The Anxiety instead of it influencing me"
- Develop your "Preferred Story" - who are you becoming?
- Identify "Supporting Cast" - who witnesses your strengths?

*Existential Exploration*
- Meaning-making prompt: "This struggle is teaching me..."
- Freedom practice: "Even though I cannot control X, I can choose Y"
- Connection ritual: Share one vulnerability with trusted family member weekly

**Months 2-3: Integration and Growth**

*ACT - Committed Action Despite Discomfort*
- Develop "Choice Point" tool - toward or away from values?
- Create Willingness Action Plan for avoided activities
- Build "Flexibility Diary" - track psychological flexibility daily

*DBT - Advanced Skills*
- Distress Tolerance: Build "Distress Tolerance Kit"
- Emotion Regulation: Complete "Emotion Regulation Worksheet"
- Create "Wise Mind" practice routine
- Develop personal "Self-Validation" statements

*Narrative - Thickening the Preferred Story*
- Document "Evidence of Change" collection
- Create "Alternative Story" timeline
- Letter to future self from preferred identity

*Existential - Deep Engagement*
- Monthly meaning review: "What made this month meaningful?"
- Mortality meditation: "If I had one year left..."
- Authenticity check: "Where am I living others' expectations?"

### Crisis Resources with Therapeutic Alignment

If overwhelm intensifies:
1. DBT Crisis Survival: STOP skill (Stop, Take a step back, Observe, Proceed mindfully)
2. ACT Crisis Response: "This is a moment of suffering. Suffering is part of human life. May I be kind to myself in this moment."
3. Narrative Crisis Reframe: "This is not who I am, this is what I'm experiencing"
4. Existential Crisis Anchor: "This too shall pass. What remains constant is my ability to choose my response."

**Professional Consultation Indicated When:**
- The Anxiety/Depression prevents values-based living for >2 weeks
- Physical symptoms interfere with daily functioning
- Thoughts of escape through self-harm emerge
- You need a witness to your re-authoring journey

### Your Resilience Factors (Don't Forget These)

- Maintained family connections despite struggle
- Confidence in problem-solving remains accessible
- Awareness of patterns (seeking help shows wisdom)
- Physical symptoms indicate sensitive, responsive nervous system (not broken, just overwhelmed)

Remember: You are not your anxiety. You are not your depression. You are the conscious awareness experiencing these temporary weather patterns of the mind. Your story is still being written, and you hold the pen.
```

### 11. Implementation Notes

#### Avoiding Cookie-Cutter Responses
```javascript
class PersonalizationEngine {
  // NEVER generate generic advice like "try deep breathing" or "exercise more"
  // ALWAYS connect interventions to specific assessment patterns
  
  validateIntervention(intervention, userData) {
    const genericPhrases = [
      "practice mindfulness",
      "try meditation",
      "exercise regularly",
      "get enough sleep",
      "eat healthy",
      "reduce stress"
    ];
    
    // Reject if too generic
    if (genericPhrases.some(phrase => intervention.includes(phrase))) {
      return this.makeSpecific(intervention, userData);
    }
    
    // Ensure intervention addresses specific symptoms
    if (!intervention.targetsSymptom || !intervention.rationaleFromData) {
      return this.addSpecificity(intervention, userData);
    }
    
    return intervention;
  }
  
  makeSpecific(genericIntervention, userData) {
    // Transform generic into specific based on data
    // Example: "practice mindfulness" becomes:
    // "When you notice The Worry Story starting (usually mornings based on your 
    // BDI responses), practice 3-minute 'Dropping Anchor' - feel feet on floor,
    // name 5 things you see, then choose one values-based action for the day"
    
    return this.specificInterventions[userData.primaryPattern];
  }
  
  ensureTherapeuticConsistency(recommendations) {
    // Check that recommendations align with therapeutic approach
    const validator = {
      ACT: (rec) => rec.includes('values') || rec.includes('acceptance') || rec.includes('flexibility'),
      DBT: (rec) => rec.includes('skill') || rec.includes('effective') || rec.includes('wise mind'),
      Narrative: (rec) => rec.includes('story') || rec.includes('The') || rec.includes('influence'),
      Existential: (rec) => rec.includes('meaning') || rec.includes('choice') || rec.includes('authentic')
    };
    
    return recommendations.filter(rec => 
      Object.values(validator).some(validate => validate(rec))
    );
  }
}
```

#### Therapeutic Voice Consistency
```javascript
const therapeuticVoice = {
  principles: [
    "Never pathologize - problems are separate from person",
    "Always acknowledge agency and choice",
    "Honor both acceptance AND change (dialectical)",
    "Recognize suffering as universal human experience",
    "Frame symptoms as protective strategies that may no longer serve",
    "Use collaborative language ('we might explore' vs 'you should')",
    "Validate before suggesting change",
    "Connect all suggestions to client's stated values"
  ],
  
  languageTransformations: {
    avoid: [
      "your anxiety disorder",
      "your symptoms",
      "you need to",
      "you should",
      "your negative thoughts",
      "dysfunctional patterns"
    ],
    prefer: [
      "The Anxiety that visits you",
      "these experiences",
      "you might explore",
      "one option could be",
      "thoughts that don't serve you",
      "patterns that once protected you"
    ]
  }
};
```

#### Performance Optimization
- Lazy load assessment modules
- Use Web Workers for complex calculations
- Implement virtual scrolling for long reports
- Cache static resources with Service Workers
- Preload therapeutic framework libraries

#### Privacy & Security
- All processing client-side only
- No data transmission to servers
- Optional encrypted local storage
- Clear data option readily available
- Therapeutic notes remain completely private

#### Browser Compatibility
- Support Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Graceful degradation for older browsers
- Progressive enhancement approach
- Mobile-optimized for therapy homework

### 12. Testing Requirements

- Unit tests for all scoring algorithms
- Integration tests for factor analyses
- E2E tests for complete user journeys
- Therapeutic language validation tests
- Cultural sensitivity review
- Accessibility testing with screen readers
- Performance testing on low-end devices
- Clinical validation against manual scoring
- Therapeutic approach fidelity testing

### 13. Adaptive Severity Response System

```javascript
class SeverityAdaptiveSystem {
  adaptResponseToSeverity(data) {
    const severity = this.calculateOverallSeverity(data);
    
    switch(severity) {
      case 'mild':
        return {
          approach: "Self-guided with periodic check-ins",
          emphasis: {
            ACT: "Values exploration and committed action",
            DBT: "Building on existing skills",
            Narrative: "Strengthening preferred story",
            Existential: "Deepening meaning and purpose"
          },
          tone: "Exploratory and growth-oriented"
        };
        
      case 'moderate':
        return {
          approach: "Structured skill-building with support options",
          emphasis: {
            ACT: "Defusion and acceptance practices",
            DBT: "Core skills training across all modules",
            Narrative: "Active externalization and re-authoring",
            Existential: "Addressing authenticity and freedom"
          },
          tone: "Supportive and skill-focused"
        };
        
      case 'severe':
        return {
          approach: "Crisis resources with immediate stabilization",
          emphasis: {
            ACT: "Basic willingness and present-moment awareness",
            DBT: "Distress tolerance and crisis survival",
            Narrative: "Finding any unique outcome",
            Existential: "Holding hope and basic meaning"
          },
          tone: "Compassionate and stabilizing",
          additionalResources: this.getCrisisResources()
        };
    }
  }
  
  personalizeByPattern(data) {
    const patterns = this.identifyPrimaryPatterns(data);
    
    // Example personalization for anxiety-dominant pattern
    if (patterns.primary === 'anxiety-somatic') {
      return {
        ACT: {
          focus: "Expansion technique for physical sensations",
          metaphor: "Making room for the anxiety storm in your body"
        },
        DBT: {
          priority: "TIPP and self-soothe for body regulation",
          sequence: "Start with temperature, then move to paced breathing"
        },
        Narrative: {
          externalization: "The Body Alarm that won't turn off",
          questions: "When has your body been calm despite stress?"
        },
        Existential: {
          exploration: "What is your body trying to protect you from?",
          meaning: "How does physical vigilance connect to what matters?"
        }
      };
    }
    
    // Continue for other patterns...
    return this.matchPatternToInterventions(patterns);
  }
}
```

### 14. Continuous Improvement Features

```javascript
class ContinuousImprovement {
  trackInterventionEffectiveness() {
    // Allow users to rate helpfulness of specific interventions
    // Adjust future recommendations based on what works
    return {
      interventionTracking: {
        tried: [],
        helpful: [],
        modified: [],
        discontinued: []
      },
      adaptiveLearning: {
        preferredFramework: "", // User gravitates toward ACT vs DBT etc
        effectivePractices: [],
        ineffectivePractices: [],
        personalAdaptations: []
      }
    };
  }
  
  generateProgressNarrative(previousSessions, currentSession) {
    // Compare across sessions to identify:
    // - Changes in problem influence (Narrative)
    // - Movement toward values (ACT)
    // - Skill acquisition (DBT)
    // - Meaning evolution (Existential)
    
    return {
      progressStory: "Your journey from [date] to now shows...",
      therapeuticWins: [],
      emergingStrengths: [],
      nextChapterPossibilities: []
    };
  }
}
```

## Deliverables

1. **Functional prototype** with all assessments and therapeutic frameworks integrated
2. **Comprehensive documentation** including:
   - Scoring algorithms
   - Therapeutic approach integration guide
   - Personalization logic documentation
3. **Therapeutic fidelity guide** ensuring accurate representation of ACT/DBT/Narrative/Existential approaches
4. **Test suite** with >90% coverage including therapeutic language validation
5. **Deployment package** for static hosting
6. **User guide** with therapeutic rationales
7. **Clinician manual** for therapists using these modalities
8. **Cultural adaptation guide** for diverse populations

## Success Metrics

- 100% accuracy in score calculation
- <3 second report generation time
- Mobile-friendly (100% responsive)
- Zero server dependencies for core functionality
- Export functionality works offline
- Passes WCAG 2.1 AA compliance
- Therapeutic language consistency >95%
- Zero generic/cookie-cutter recommendations
- Personalization depth score >8/10
- User perception of relevance >85%
- Clinician approval of therapeutic fidelity >90%
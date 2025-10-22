Website says: "Our applications are typically 5 pages long."

The proposal text must be written in English and should clearly describe the following aspects of the proposed seminar:

    // For resubmissions: Overview of what changed as well as a discussion of the feedback received and how you addressed it
    // For Dagstuhl Perspectives Workshops: A concept for the Dagstuhl Manifesto and/or a plan of how it would be created

    Summary of the field(s) of research within which the topic of the proposed seminar lies

Over the past decade, the Rust programming language has been gaining traction as an alternative
to languages such as C or C++ for low-level, security-critical programming. This success especially
stems from several key features of the language: Rust combines the low-level idioms and performance
commonly associated to C or C++ with memory safety by construction thanks to its rich, ownership-based
type system. Nowadays, Rust is therefore at the forefront of the Safe Coding methodology, with both
governments and corporations advocating to a transition to Rust to guarantee the safety
and reliability of critical software infrastructure; as an example, high-profile projects such as
the Windows and Linux kernels are currently developing new features using Rust.

Despite its promises, using Rust is however not a silver bullet. First, to ensure memory safety,
Rust relies on runtime checks to determine whether accesses into structured memory (i.e., into arrays)
are in bounds; if not, programs cleanly abort (panic in Rust parlance). While better than memory vulnerabilities
in C or C++, this behavior is however limiting, necessiting programmers to establish the _panic-freedom_ of their code.
Second, while highly effective, the Rust _borrow-checker_, in charge of ensuring that Rust code abides by the
ownership-based discipline underlying memory safety can be too restrictive. To work around this, Rust therefore provides
an _unsafe_ escape hatch, allowing for more complex aliasing and memory patterns, at the cost of compile-time safety
guarantees. Last, beyond safety, Rust does not guarantee the _correctness_ of the codebases, leading to a flurry
of potential issues.

To solve these issues, the formal verification community recently started investigating the development of
static analysis and deductive verification tools, aiming to further raise the confidence and reliability
of newly developed, security-critical Rust code. Many teams either repurposed and extended existing, well-established
tools for other languages (e.g., C) to target Rust, or developed new approaches specifically targeting Rust
specificites, leveraging invariants provided by the type system to simplify analyses and verification.
//AF: Do we need explicit citations/names here?

While several of these approaches are now able to handle complex applications, e.g., cryptographic implementations,
operating systems, security monitors, or the Rust standard library itself, the multiplicity of tools leads to
duplicated work, both in terms of approaches and program logics being developed, but also in the engineering
infrastructure needed to parse Rust programs and interact with existing Rust compilation toolchains (i.e., rustc)
to extract the semantic information needed to efficiently reason about programs. To assist with the widespread transition
to safe Rust coding, it is therefore paramount gather the Rust formal verification community in order to share ideas
and implementation efforts, and identify impactful targets for novel analyses and verification tools.

    Description of the seminar topics

This seminar will focus on applications of formal verification to the Rust programming language and ecosystem.
To do so, we will work around three main axes.

1. Existing tools and ongoing developments
Overview of existing approaches, duplication, create new connections
Common engineering problems, interaction with Rust compiler and compiler developers
How to leverage a rich literature on formal verification in other languages?

2. Emerging targets and properties
Survey of common vulnerabilities, identification of missing analysis and verification targets
Discussion around emerging Rust applications, threat models considered, and how to accompany the ongoing trend
of transitioning to Rust

3. Rust foundations
Semantics of the language and borrow-checker, and how to use it as a basis to establish the soundness
of verification tools, and develop new program logics.

    Composition of the organizing team

List 4 participants, emphasize different tools, approaches.

    Expected results (outcome) of the seminar

List of concrete problems related to interactions with Rust limiting tools expressiveness and effectiveness
Survey of the state of Rust semantics and foundations for verification and analysis tools
Taxonomy of Rust vulnerabilities and pitfalls, as well as formal properties of interest to prevent them
Benchmarking suite for static analysis (covering different Rust features, common classes of vulnerabilities identified above), and
    "proof ladder" for deductive verification tools, fostering comparison and development of tooling
Common, shared engineering infrastructure to develop new tools for Rust

    Ideas about the structure of the seminar

Aim for a short seminar (3 days):
    Day 1, morning: Quick presentations from all participants (20 minutes) about their tools, scope, expressiveness, and common difficulties interacting with Rust

    All working groups come with a summary to the broader audience at the end of the session
    Day 1, afternoon: Working Groups
        * Survey of RUSTSEC to distill common classes of vulnerabilities
        * Overview of the Rust semantics, and missing/misunderstood concepts
        * Discussion of common specification language for Rust

    Day 2, morning: Working groups
        * Suite of testcases for common classes of vulnerabilities
        * Focus groups for new analyses areas
        * Discussion of well-established C verification tools, and connections/applicability to Rust
        * Interacting with the Rust compiler, and common engineering challenges

    Day 2, afternooon:
        * "VerifyThis"-like challenge for deductive verification tools
        * "AnalyzeThat"-like challenge for static analysis tools, using testcases established in the morning

    Day 3, morning:
        * Debrief of differences, strengths and weaknesses of existing tools, based on day 2 challenge

    Day 3, afternoon:
        * Hacking on common engineering infrastructure
        * Prototypes of novel analyses
        * Larger benchmarking suite and proof ladder for different tools


    Difference to other Dagstuhl Seminars within related topics, in particular those within the same topic

Focus on Rust.
(check other Dagstuhl seminars, especially related to abstract interpretation/program analysis)
-> Nothing on Rust in 2024 to 2027

    Conferences and research projects within related topics, and why it is justified to hold such a seminar at Dagstuhl

RustVerify -> Focus on presenting tools, no time for deep dive into challenges/discussion/hacking


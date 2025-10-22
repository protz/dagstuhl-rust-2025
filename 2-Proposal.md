Website says: "Our applications are typically 5 pages long."

The proposal text must be written in English and should clearly describe the following aspects of the proposed seminar:

    // For resubmissions: Overview of what changed as well as a discussion of the feedback received and how you addressed it
    // For Dagstuhl Perspectives Workshops: A concept for the Dagstuhl Manifesto and/or a plan of how it would be created

    Summary of the field(s) of research within which the topic of the proposed seminar lies

Rust is important, growing interest in governments/industry.
Many teams spread throughout the world on analysis/verification, few shared efforts, repetition of work

    Description of the seminar topics

Focus on tools, engineering, semantics underlying the soundness of the tools, as well as concrete outcomes for
securing existing Rust code

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


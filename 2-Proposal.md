Website says: "Our applications are typically 5 pages long."

The proposal text must be written in English and should clearly describe the following aspects of the proposed seminar:

# Summary of the field(s) of research within which the topic of the proposed seminar lies

Over the past decade, the Rust programming language has been gaining traction as an alternative
to languages such as C or C++ for low-level, security-critical programming. This success stems in
large part from several key features of the language: Rust supports the low-level idioms and performance
commonly associated with C or C++ while providing memory safety by construction thanks to its rich, ownership-based
type system. As a result, Rust is now at the forefront of the Safe Coding methodology, with both
governments and corporations advocating for a transition to Rust in order to guarantee the safety
and reliability of critical software infrastructure; as an example, high-profile projects such as
the Windows and Linux kernels are currently developing new features using Rust.

Despite its promises, however, using Rust is not a silver bullet. First, to ensure memory safety,
Rust relies on runtime checks to determine whether accesses into structured memory (i.e., into
arrays) are in bounds; if not, programs cleanly abort (panic in Rust parlance). While better than
memory vulnerabilities in C or C++, this behavior obliges programmers to manually establish the
_panic-freedom_ of their code.  Second, while highly effective, the Rust _borrow-checker_ can be too
restrictive in its quest to ensure that Rust code abides by the ownership-based discipline
underlying memory safety.  To work around these restrictions, Rust provides an _unsafe_ escape
hatch, allowing for more complex aliasing and memory patterns, at the cost of compile-time safety
guarantees. Last, beyond safety, Rust does not guarantee _correctness_, _reliability_, or
_security_, leaving Rust code potentially susceptible to a range issues.

To address these issues, the formal verification community recently started investigating the development of
static analysis and deductive verification tools, aiming to further raise the confidence and reliability
of newly developed, security-critical Rust code. Many teams either repurposed and extended existing, well-established
tools for other languages (e.g., C) to target Rust, or developed new approaches specifically targeting Rust
specificities, in both cases leveraging invariants provided by the type system to simplify analysis and verification.
//AF: Do we need explicit citations/names here?

While several of these approaches are now able to handle complex applications, e.g., cryptographic implementations,
operating systems, security monitors, or the Rust standard library itself, the multiplicity of tools leads to
duplicated work, in both the approaches and program logics being developed, and also in the engineering
infrastructure needed to parse Rust programs and interact with existing Rust compilation toolchains (i.e., `rustc`)
to extract the semantic information needed to efficiently reason about programs. To assist with the widespread transition
to safe Rust coding, it is therefore paramount to gather the Rust formal verification community in order to share ideas
and implementation efforts, and identify impactful targets for novel analyses and verification tools.

# Description of the seminar topics

This seminar will focus on the theory and practice of Rust formal analysis. Specifically, we will
focus on three intertwined problems: first, the theoretical foundation of Rust; second, the
theoretical foundation for Rust analyses; and third, the engineering practices and tool ecosystem that
implement those analyses.

For Rust foundations, the situation remains, to this day, that many corners of the language are
ill-defined. While foundational work (notably, RustBelt) has succeeded in shoring up the theoretical basis of the
language, many corners of the language remain unexplored (from a foundational
perspective), such as its trait system. Furthermore, several attempts at improving the Rust language
have stalled, either because of the lack of confidence in how they interact with the rest of the
language in terms of soundness, or simply because enunciating their theory cleanly and neatly
remains difficult, for lack of a good reference semantics for the language. Examples include the
view types proposal (never implemented), ongoing rewrites of the borrow checker (still not ready to
be merged), or a proposal for a new trait system for Rust (whose behavior differs from the previous
implementation, but which, lacking a formal model, cannot be conclusively determined to be the
correct behavior).

It therefore remains difficult to confidently develop analyses, or reason about Rust programs, when
the semantics of Rust are still undergoing such debate. For these reasons, the semantics of the
language and its borrow-checker, and in particular, how to form a basis to establish the soundness
of verification tools, will be the first focus of this seminar.

Next, many analyses try to leverage Rust's unique ownership discipline to simplify reasoning, or to
make implementations more efficient. We propose to focus, as a second axis, on a broader re-thinking
of existing analyses in the context of Rust; how Rust's ownership impacts, e.g., resource analysis
(as exemplified by RaRust), property-based testing, and many other analyses. While existing program
verification frameworks do leverage ownership as a means to automate and/or simplify reasoning, we
believe there is more potential to be tapped in order to make the analysis of Rust programs
generally more efficient thanks to the ownership guarantees offered by the language.
PM: what does "meaningful" mean here?
JP: tried to rephrase

As a third axis, we propose to focus specifically on tooling. There is a considerable amount of
design and implementation work that needs to be addressed in this area, notably:
- Many analyses re-implement a frontend to the Rust compiler at considerable engineering cost; could
  the community standardize on one framework (such as the Charon project), and if not, what
  are the roadblocks?
- What needs to be implemented in the Rust compiler to make analyses easier to implement?
- What is the status of the Rust specification language?  Can progress on this specific point happen
  through focused working session as part of this Rust seminar?
PM: related to my comment about "engineering" below, I would emphasize "concepts", "algorithms", etc. and
de-emphasize "implementation".


Finally, as a transversal axis, we propose to put all of the ideas above in practice by identifying
common vulnerabilities, new threat models, and from there on, forming a list of missing analyses and
verification targets which could be implemented as end-to-end results that rely on improvements
along all three axes above.
PM: Do we want to give this seminar a security spin, or does "vulnerabilities" include correctness bugs?
BP: I agree; "vulnerabilities" and "thread models" are very security specific.  I love security, but
    should we cast a wider net here?

We remark that browsing the Dagstuhl archives, we could not find a single seminar focusing on Rust
specifically; given the excitement about Rust in the research community, we think it is timely and
important to gather researchers on this particular topic as soon as possible!

<!-- 1. Existing tools and ongoing developments -->
<!-- Overview of existing approaches, duplication, create new connections -->
<!-- Common engineering problems, interaction with Rust compiler and compiler developers -->
<!-- How to leverage a rich literature on formal verification in other languages? -->

<!-- 2. Emerging targets and properties -->
<!-- Survey of common vulnerabilities, identification of missing analysis and verification targets -->
<!-- Discussion around emerging Rust applications, threat models considered, and how to accompany the ongoing trend -->
<!-- of transitioning to Rust -->

# Composition of the organizing team

Our organizing team represents a broad cross-section of the Rust analysis community, with four
different tools represented (Verus, Prusti, Charon, and Aeneas), a variety of seniority levels,
geographical diversity (two US and two European organizers), and one industry member who has been
involved in driving verified Rust code into production.

The variety of tools also reflects a variety of approaches:
- the Verus Rust verifier emphasizes an SMT-first approach while leveraging Rust's ownership to
  efficiently encode Rust programs to SMT 
- the Prusti Rust verifier relies on the Viper infrastructure, where Rust's ownership discipline
  guides the application of rules in separation logic
- the Aeneas Rust verifier relies on backwards functions to translate Rust programs into a pure
  equivalent that is sent to an interactive prover, with a particular emphasis on Lean.

We believe this variety will prevent one particular style from being over-represented, and will
encourage a broad discussion of possible approaches.

Finally, two of the organizers have significant experience with the Charon Rust analysis toolkit,
which is currently used by several tools, notably Aeneas (Rust verifier), Eurydice (Rust to C
compiler), RaRust (Rust resource analysis), and several more.


# Expected results (outcome) of the seminar

We expect several outcomes, in no particular order:
- a list of concrete engineering problems that ought to be fixed in Rust to facilitate tool
  expressiveness and effectiveness;
- additional and/or improved common, shared engineering infrastructure to develop new tools for Rust
- new lines of work towards clarifying the semantics of Rust and ultimately improving the language
  specification;
- a survey (or SoK) on the state of Rust verification and/or analysis tools;
- a taxonomy of Rust vulnerabilities and pitfalls, as well as formal properties of interest to
  prevent them -- this could foster new avenues for fresh research
- a benchmarking suite for static analysis (covering different Rust features, common classes of
  vulnerabilities identified above), and a "proof ladder" for deductive verification tools, fostering
  comparison and development of tooling

PM: I would de-emphasize "engineering" in the proposal. We all agree on the importance of tool development, but many
academics interpret "engineering" as the opposite of "science" ("something is *just* engineering").

PM: We might want to make the distinction between safe and unsafe Rust more explicit. One can view most of the verification work
on Rust as either (1) leveraging the guarantees of safe Rust to make verification simpler, or (2) proving that unsafe Rust is 
actually safe and has the intended behavior. For many practical applications, tools will have to support both, but it is an open
problem how to get there.

BP: I'm not sure SoK is a sufficiently well-known acronym to use here.

BP: Same concern as above re: "vulnerabilities"

BP: What is a "proof ladder"?
JP: set of representative examples in order of increasing difficulty

BP: Some additional ideas:
- A shared understanding of the advantages and disadvantages of existing analysis techniques
- New directions for combining the best ideas from existing analysis techniques
- A call to arms for formalization experts, pointing them at critical, understudied places in the Rust language
- New ideas for increasing adoption of these tools and techniques by the Rust community

# Ideas about the structure of the seminar

Aim for a short seminar (3 days):

    Day 1, morning: Quick presentations from all participants (20 minutes) about their tools, scope, expressiveness, and common difficulties interacting with Rust

BP: 20 minutes each, right?
JP: yes

    All working groups come with a summary to the broader audience at the end of each session
    Day 1, afternoon: Working Groups
        * Survey of RUSTSEC to distill common classes of vulnerabilities (BP: Same as above re: vulnerabilities)
        * Overview of the Rust semantics, and missing/misunderstood concepts
        * Discussion of a common specification language for Rust

    Day 2, morning: Working groups
        * Suite of testcases for common classes of vulnerabilities
        * Focus groups for new analysis areas
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

PM: I the afternoon of day 3 realistic? 
BP: It does seem like a lot for an afternoon
JP: I think we were envisioning parallel sessions where people can join one or the other

BP: For Day 2 afternoon, is it realistic that we can come up with good analysis/verification targets
    in the morning?  Or are we going to have to prepare something in advance?  Both seem potentially
    fraught.

    Difference to other Dagstuhl Seminars within related topics, in particular those within the same topic

Focus on Rust.
(check other Dagstuhl seminars, especially related to abstract interpretation/program analysis)
-> Nothing on Rust in 2024 to 2027

BP: What about before 2024?
JP: nothing either, I went through all of the archives 
BP: Are there non-Rust seminars on analysis + verification for other
languages?

# Conferences and research projects within related topics, and why it is justified to hold such a seminar at Dagstuhl

RustVerify -> Focus on presenting tools, no time for deep dive into challenges/discussion/hacking


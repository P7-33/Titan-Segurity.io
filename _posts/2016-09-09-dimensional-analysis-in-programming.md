---
title: 'Dimensional Analysis in Programming Languages'
date: 2020-01-26T07:12:00+01:00
draft: false
---

[Research](https://gmpreussner.com/research) May 24, 2018

Dimensional Analysis in Programming Languages
=============================================

A survey of existing designs and implementations for automatic conversion and verification of units of measurement in computer programs.

Tags: [programming](https://gmpreussner.com/research/tag:programming)

Overview
========

[Dimensional analysis](https://en.wikipedia.org/wiki/Dimensional_analysis "Wikipedia: Dimensional Analysis") is a technique for comparing and calculating with numerical quantities in which units are included and treated algebraically. This article clarifies the basic concepts and looks at how they have been implemented in various programming languages.

Motivation
----------

Opinions differ as to whether dimensional analysis should be implemented as a language feature, a library, or at all. One thing that most engineers do agree on is that there is great value in compilers verifying the correctness of programs before they are executed. The ability to automatically check the usage of units of measurement can eliminate an entire class of errors and potentially prevent [all sorts of disasters](http://mentalfloss.com/article/25845/quick-6-six-unit-conversion-disasters "Mental Floss: Six Unit Conversion Disasters"). What is less clear is how this should be accomplished in practice.

If you've used strongly-typed programming languages before, the relationship between dimensional analysis and type theory is rather obvious. Using types to represent measurement systems is in fact the most popular implementation approach, but not everyone agrees that the added structure and complexity is worth the effort. The controversy mainly revolves around convenience. When is a type system beneficial, and when does it get in the way? John D. Cook [pointed out](https://www.johndcook.com/blog/2015/12/01/dimensional-analysis-and-types/) that it mainly depends on your use case. It also depends on how expressive the language is and how much machinery is needed to make it work.

I mostly work in large code bases myself. These aren't necessarily mission critical in the sense that lives depend on them, but reliability still is a desirable property from a business point of view. Other [software qualities](https://en.wikipedia.org/wiki/Software_quality "Wikipedia: Software quality") that are often overlooked are comprehensibility and maintainability. In an economic system that rewards time to market, the long-term costs of software development are rarely considered. By adding dimensional analysis to code we have an opportunity to make it easier to read, understand, refactor and extend. This is increasingly important as projects grow larger over time.

Concepts
--------

Different authors use slightly different terminology in the literature for dimensional analysis, so it might be worthwhile to clarify the concepts.

**Physical dimensions** (also: _dimensions_) are distinct kinds of observable characteristics of objects or events that can be directly compared to one another, i.e. _length_, _mass_, and _electric charge_. Even though there is strong agreement about which dimensions form the foundation of the natural sciences, they are nevertheless a matter of convention. For instance, electrical properties were not taken into consideration until the 1800's.

**Measurements** are the assignments of numbers (also: _measures_, _values_, or _magnitudes_) to the characteristics of objects or events within a given _dimension_. Since physical characteristics cannot be described in absolute terms they must be compared by reference to other objects or events. For example, we can determine that some object has the same length as, or twice the mass of another object. The process of measuring can be simple or involved, but the numbers assigned as a result are always ratios of the objects' characteristics within the dimension of interest.

**Base units** are characteristics of _particular_ objects or events that are selected as a reference for taking _measurements_ in a given dimension. In practice, most base units are derived from invariant constants of nature that can be measured with great accuracy, but it is important to note that they, too, are a matter of convention. For example, _second_ is the base unit for measuring time in the SI system and defined in terms of radiation properties of Caesium 133 atoms. Base units are chosen in such a way that they cannot be derived (are mutually independent) from each other.

**Derived units** are defined in terms of _base units_ or other derived units by combining them via multiplication or division. If _meter_ and _second_ are chosen as base units, _meter2_ and _meter/second_ would be derived units.

**Unit exponents** (also: _exponents_) are positive or negative numbers for the powers of base units that make up a _derived unit_. For example, _voltage_ is derived from the base units kilogram, meter, second, and ampere, and the exponents are 1, 2, -3, and -1 for kg×m2×s−3×A−1. In practice, the vast majority of exponents are in the range -4 to +4, inclusive. Exponents are usually integral, but some computations involve rational exponents.

**Units of measurement** (also: _units_, _units of measure_) are _base units_ or _derived units_. Physical dimensions may have multiple units, for example, _meter_ and _inch_ are both units of length. Units may contain multiplicative factors, for example, one _inch_ is 0.0254 meters. Units are said to be _coherent_ if they do not contain any numerical factors other than 1. Units may also contain zero point shifts as in _celsius_ and _fahrenheit_, which are both units of temperature. These are sometimes called _affine units_.

**Unit symbols** (also: _symbols_) are letters or signs assigned to _units of measurement_ so that the latter can be expressed more concisely. For example, in the SI system, _m_ is the symbol for meter (the unit of length), and _J_ (Joule) is the symbol for kg×m2×s−2 (the unit of energy).

**Prefix names** (also: _prefixes_) are words added to unit names to produce multiples and sub-multiples (usually powers of ten or a thousand) of the original unit. For example, the SI system defines the standard prefix names _kilo_ for 103 and _milli_ for 10\-3, so that _kilometer_ is equal to one thousand meter, and _milligram_ to one thousands of a gram. Prefixes are never combined, i.e. _micrometer_ is used instead of _millimillimeter_.

**Prefix symbols** are short versions of _prefix names_ that are attached to _unit symbols_, for example, _k_ for kilo and _m_ for milli, so that kilometer can be written as _km_, and milligram as _mg_.

**Physical quantities** (also: _quantities_) are characteristics of objects or events that can be quantified by measurements. They can be represented as a combination of magnitude, usually a real number, and _unit_. For example, the quantity _1.6749×10−27 kg_ is the mass of a neutron. Physical quantities that have the same dimension are said to be _commensurable_ and can be directly compared to each other even when expressed in different units of measure. Quantities measured in base units are _base quantities_. Quantities that do not have a physical dimension associated, such as angles, ratios, or percentages are called _dimensionless quantities_.

**Systems of measurements** are sets of _units of measurement_ that form a framework for comparing _physical quantities_. Such systems may or may not be coherent. The modern SI system was designed to be coherent, but the Centimetre–gram–second (CGS) system is not because it contains _calorie_ as a unit of energy, which is not coherent with its other base units. Systems of measurement may include definitions for _unit symbols_ and _prefixes_.

**Dimensional analysis** is the analysis of the relationships between different _physical quantities_ by identifying their _base quantities_ and _units of measure_, and tracking these as calculations or comparisons are carried out. Historically, it is used to simplify physical problems before obtaining a quantitative answer. In computer programs it can be used to verify the semantic consistency of scientific algorithms.

An important theorem in dimensional analysis is the _Buckingham π theorem_, which states that the laws of physics do not depend on the choice of a specific system of measurement. One should also note that, even though dimensional analysis is usually associated with scientific calculations and the definitions above rest on examples from physics, it is not limited to physical quantities, but applicable to any kind of units, practical or not.

The theoretical foundations of dimensional analysis and its application in the natural sciences are well explained in Sonin's paper on [The Physical Basis of Dimensional Analysis](http://web.mit.edu/2.25/www/pdf/DA_unified.pdf). In the rest of this article we will take a look at how it is implemented in existing software systems.

Languages
---------

We already considered the use of the type systems of programming languages to represent units of measurement. However, the label notation that is commonly taught in school, and that most of us are familiar with, does not lend itself to the syntactic requirements of most languages. The resulting code can be awkward or cumbersome to use. It is therefore tempting to build syntactic support for dimensions and units into the language itself.

Surprisingly, there aren't many programming languages that actually do this. At the time of this writing, the only mainstream language with built-in support appears to be [F#](https://gmpreussner.com/research/dimensional-analysis-in-programming-languages#fsharp). The other big contenders are [ATLAS](https://gmpreussner.com/research/dimensional-analysis-in-programming-languages#atlas), [Fortress](https://gmpreussner.com/research/dimensional-analysis-in-programming-languages#fortress) and [Frink](https://gmpreussner.com/research/dimensional-analysis-in-programming-languages#frink). We'll look at these in more detail below.

Libraries
---------

Many argue that dimensional analysis is a domain specific feature that does not belong into the programming language itself, but is best left to be implemented in libraries. Ideally, a programming language is as concise and general as possible while also providing mechanisms for expressing domain specific concerns in a convenient and readable way.

Even though most of today's mainstream languages are still significantly handicapped in this regard, there has been no lack of implementation attempts. It is worthwhile to study the most popular libraries and see what they offer, how they differ, and the limitations they have.

Research
--------

Research for the incorporation of units into programming language goes all the way back to the 60's. A more general discussion has been presented as early as 1978 by [Karr & Loveman](https://dl.acm.org/citation.cfm?doid=359488.359501 "ACM Digital Library: Incorporation of Units Into Programming Languages"). After reviewing units calculus, their paper introduces units as sub-types and covers syntactical issues. Much of it is still relevant today.

There have also been attempts to infer unit types automatically without any annotations, such as by [Wand & O'Keefe](http://www.ccs.neu.edu/home/wand/papers/dimensions.ps "PS: Automatic Dimensional Inference") for ML, and [Guo & McCamant](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-883-program-analysis-fall-2005/projects/unit_type_infere.pdf "PDF: Annotation-less Unit Type Inference for C") for C. [Bruche Hamilton](http://www.hpl.hp.com/techreports/96/HPL-96-61.pdf) discussed the general representation of units in and between computer systems.

The following sections will give an overview of particular implementation examples in various programming languages. It is not my goal to provide an exhaustive list and analyze or evaluate each of them in detail, but rather to point out certain design decisions, features, and syntactic choices.

Ada
===

Dimensional analysis support in Ada has been researched since the mid 80's, and there have been a number of proposals. Grein et. al. published a [survey of physical unit handling techniques](https://link.springer.com/chapter/10.1007/3-540-44947-7_19) in 2003, discussing the contradictory requirements of compile-time methods, as well as the implementation and shortcomings of existing solutions. The problem was solved more generally (and with some compromises) in the GNAT dimension system in 2012.

Gehani
------

In 1985, N. H. Gehani's presented two ideas for [units of measure in Ada](https://dl.acm.org/citation.cfm). His first implementation uses distinct derived types in combination with operator overloading:

```
type SPEED is new FLOAT; type ACCELERATION is new FLOAT; type TIME is new FLOAT; type DISTANCE is new FLOAT; function "*"(A:SPEED;B;TIME) return DISTANCE is begin return DISTANCE(A) * DISTANCE(B); end "*"; function "*" (A:ACCELERATION; B:TIME) return DISTANCE is begin return DISTANCE(A) * DISTANCE(B); end "*"; U: SPEED; A: ACCELERATION; T: TIME; S: DISTANCE; S:= U * T + 0.5 * A * (T * T);
```

Gehani shows that this is approach is not sufficient for modelling an algebra with units as it disallows certain operations that should be permitted and vice versa.

After considering language modifications and preprocessors, his second implementation is a library package that introduces integer and floating-point quantity types that store a unit name and exponent along with values, and a set of operators and helpers for assignments and conversions:

```
AREA: FLOAT-WITH-UNITS:= (0.0, 1, ((METER, 2))); SIDE: FLOAT-WITH-UNITS:= (5.0.1. ((METER, 1))); S1, S2: FLOAT-WITH-UNITS:= (0.0, 2, ((MILE, 1), (HOUR, -1))); ASSIGN(AREA, SIDE*SIDE);
```

This notation considerably differs differs from what scientists are acustomed to, and Gehani's approach also has some other problems. A detailed critique can be found in R. T. House's proposal for [type checking of expressions](https://dl.acm.org/citation.cfm) ([PDF](https://academic.oup.com/comjnl/article-pdf/26/4/366/1072622/26-4-366.pdf)).

GNAT
----

In 2012, Vincent Pucci and Ed Schonberg added support for physical units with [simple dimensionality checking](https://blog.adacore.com/uploads/dc.pdf) at compile-time to AdaCore's GNAT compiler. The system provides base and derived MKS units and symbols with zero run-time overhead. It has support for fractional dimensions and basic I/O. Prefixed units are represented as constants.

Unit systems are defined via two aspects, `Dimension` and `Dimension_System`, which can also be used for defining custom units. The details and some examples are explained in [Pucci's blog post](https://www.adacore.com/gems/gem-136-how-tall-is-a-kilogram "AdaCore Blog: How tall is a kilogram?").

The following is an excerpt of the MKS system definition:

```
type Mks_Type is new Long_Long_Float with Dimension_System => ( (Unit_Name => Meter, Unit_Symbol => 'm', Dim_Symbol => 'L'), (Unit_Name => Second, Unit_Symbol => 's', Dim_Symbol => 'T'), ... subtype Length is Mks_Type with Dimension => (Symbol => 'm', Meter => 1, others => 0); subtype Time is Mks_Type with Dimension => (Symbol => 's', Second => 1, others => 0); m : constant Length := 1.0; s : constant Time := 1.0; cm : constant Length := 1.0E-02; km : constant Length := 1.0E+03; min : constant Time := 60.0 * s; hour : constant Time := 60.0 * min; subtype Area is Mks_Type with Dimension => ( Meter => 2, others => 0); subtype Speed is Mks_Type with Dimension => ( Meter => 1, Second => -1, others => 0);
```

The defined units can then be used in program code (excerpt from GNAT):

```
procedure Foo is subtype Acceleration is Mks_Type with Dimension => ("m/sec^2", 1, 0, -2, others => 0); G : constant Acceleration := 9.81 * M / (S ** 2); T : Time := 10.0 * S; Distance : Length; begin Distance := 0.5 * G * T ** 2; Put (Distance, Aft => 2, Exp => 0); end Foo
```

The original implementation allowed for generic programming, but left it unchecked for dimensionality correctness. This was later [improved](https://blog.adacore.com/physical-units-pass-the-generic-test "AdaCore Blog: Physical Units Pass the Generic Test") by Moy, Becker, and Regnath. Note that identifiers in Ada are case-insensitive, so the above example (`M` vs. `m`, `S` vs. `s`) still works. This and other minor shortcomings along with suggested improvements were [discussed by Grein](http://www.christ-usch-grein.homepage.t-online.de/Ada/Dimension/Physical_units_with_GNAT_GPL_2013-AUJ35.1.pdf "Physical Units with GNAT (PDF)").

UNITS
-----

In 1988, Paul N. Hilfinger published a paper that demonstrates [dimensional analysis in Ada](https://dl.acm.org/citation.cfm) based on Gehani's approach using the language's existing abstraction facilities like operator overloading and type parameterization. His _UNITS_ package allows for declaring variables, constants, and parameters with particular units of measure and arithmetic operations between them.

The following code snippet shows the syntax for declaring base unit types, a constant, variables, and function parameters:

```
subtype DISTANCE is QUANT(i,O,O,O); subtype TIME is QUANT(O,l,O,O); GRAVITY : constant QUANT := 980.7 * CM / SEC**2; x,y : DISTANCE := 0.0 * CM; V : VELOCITY := 0.0 * (CM / SEC); function HEIGHT(X : DISTANCE) return DISTANCE is -- implementation goes here end HEIGHT; 
```

`QUANT` is a generic value-with-units type for defining concrete unit subtypes. It uses Ada's constant folding to evaluate the discriminants at compile-time. It is limited to a total of four integral dimensionalities.

ATLAS
=====

C/ATLAS
-------

One of the early high-level programming languages with support for units is [C/ATLAS](https://en.wikipedia.org/wiki/Abbreviated_Test_Language_for_All_Systems "Wikipedia: ATLAS"), which was originally created in 1968 for the automated testing of avionics equipment. It has a fixed set of physical units and operations to model signal flows and common electrical and mechanical systems.

The following statement applies an alternating current of 7.5 volts at 3 kilohertz to a pin called _AC SIGNAL_:

```
010200 APPLY, AC SIGNAL, VOLTAGE-PP 7.5V, FREQ 3 KHZ, CNX HI=P1-1 $
```

ATLAS 2000
----------

After several IEEE standard iterations of _C/ATLAS_ that culminated in [IEEE 716-1995](https://standards.ieee.org/findstds/standard/716-1995.html "IEEE Standards Association: 716-1995"), the language was restructured into [ATLAS 2000](http://ieeexplore.ieee.org/document/713433/). The signal modelling aspects moved into a new language called [SMML](https://web.archive.org/web/20051110020029/http://grouper.ieee.org/groups/scc20/atlas/SMMLusers_manual.doc "System Signal Method Modeling Language User's Manual"). It uses a more familiar syntax, but still doesn't allow for extending the built-in units.

The following sample declares a voltage input signal and then applies a 20 hertz sine wave at 2 volts and zero phase to it:

```
inp:: SignalRep Time Voltage inp = sine(V 2.0)(Hz 20)(Rad 0.0)
```

There are a total of 41 predefined physical types, each with its own unit. Units always start with an upper-case letter, regardless of physical convention. Some are overloaded with prefixes, i.e. `Hz`, `Khz` and `Mhz`.

C
=

C is still one of the most widely used programming languages today. Compared to many modern languages, its type system is arguably more limited when it comes to abstraction capabilities. Nevertheless, support for dimensional analysis has been studied and exists via pre-processors.

C-UNITS
-------

In 2003, Grigore Rosu and Feng Chen published a prototype for [certifying measurement unit safety policies](https://pdfs.semanticscholar.org/4466/ee6fdb08c4f9761385da05510dac65c93095.pdf) that is based on [Maude](http://maude.cs.uiuc.edu/overview.html "Maude Project Page"), a framework for program specification and verification, and consists of both a static and a dynamic checker. It uses a _Maude_ specification to declare units of measure within the C programming language, and a special `/*U U*/` comment syntax for annotating the code.

The following snippet was taken from the paper to demonstrate the annotation of functions and variables:

```
float lb2kg(float w) /*U assert unit(w) = lb U*/ /*U assume returns kg U*/ { return 10 * w / 22; } float projectilex, projectiley; projectilex = 0; /*U assume unit(projectilex) = meter U*/ projectiley = 0; /*U assume unit(projectiley) = unit(projectilex) U*/
```

The system's dynamic checker interprets the enriched C program and checks the units of variables when they are evaluated. This adds some storage and run-time overhead. The static checker covers all reachable code, but may generate a large number of false alarms in the absence of annotations.

Guo & McCamant
--------------

In 2005, Philip Guo and Stephen McCamant presented a technique for [annotation-less type inference for C](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-883-program-analysis-fall-2005/projects/unit_type_infere.pdf "PDF: Annotation-less Unit Type Inference for C") that automatically assigns and verifies unit types to all of a program's variables.

One interesting aspect of their tool is that it does not assume any particular unit system, but instead builds up a set of constraints over all variables based on static code analysis. From these, a system with the minimum number of unspecified base units is then constructed. The user may, but is not required to annotate them with more specific names.

This approach has the major advantage that programmers can construct a complete unit typing with a minimal number of annotations. It also allows for verifying the unit correctness of existing programs without modifying the programs themselves.

For example, take the following C program:

```
int main() { double mass, velocity, height, kinetic, potential; /* ... initialize relevant variables ... */ kinetic = 0.5 * mass * velocity * velocity; potential = mass * height * 9.8; printf("Total energy is: %g J\n", kinetic + potential); return 0; }
```

Based on the constraints imposed by the addition and multiplication operations in this code, the tool may produce the following results:

```
Variables: 1: velocity Units: (unit 1) 2: mass Units: (unit 2) 3: constant 0.5 Units: (unit 3) 4: constant 9.8 Units: (unit 4) 5: height Units: (unit 1)^2 * (unit 3) * (unit 4)^-1 6: kinetic, potential Units: (unit 1)^2 * (unit 2) * (unit 3)
```

Since the inferred unit names are largely meaningless, the user may annotate them with physics terms, such as:

```
Variables: 1: velocity Units: meter second^-1 2: mass Units: kilogram 3: constant 0.5 Units: dimensionless 4: constant 9.8 Units: meter second^-2 5: height Units: meter 6: kinetic, potential Units: kilogram meter^2 second^-2
```

In practice, only four of the six units need to be annotated, because the tool can infer the derived units automatically. These annotations are then used for human readable error messages when parsing additional code.

Osprey
------

The [Osprey](http://web.cs.ucdavis.edu/~su/unitfull.pdf "PDF: Osprey: A Practical Type System for Validating Dimensional Unit Correctness of C Programs") type system adds special unit annotations to C code that are parsed and converted to type constraints and evaluated at compile time. The system focuses on the SI system of measurement and implements the seven base units from which all other scientific units can be derived.

Unit annotations start with a `$` character and support superscripts for exponentiation. Some units also have aliases, such as `kilogram` and `kg`. The special unit type `$unity` is used for dimensionless units.

The following code declares a variable 'length' with base unit 'meter', a variable 'energy' with derived units, and a structure containing a dimensionless quantity.

```
$meter double length; $kilogram*meter²*second⁻² double energy; typedef struct { $kilogram double atomicWeight; $unity double atomicNumber; } Element;
```

A constraint resolution algorithm uses these annotations to verify the correctness of the rest of the program.

Unitc
-----

[unitc](https://github.com/magnusjonsson/unitc "unitc on GitHub") is a pre-processor written in Haskell with unit annotations in a different syntax. The following is a valid program that declares annotated velocity and time variables and computes an acceleration from them:

```
double v unit(m/s); double t unit(s); double a unit(m/s/s) = v / t;
```

The current implementation only supports base units. These are not hard-coded, but derived from the annotations. It doesn't support prefixes or aliases, and the notation for exponentiation is rather limiting.

C++
===

As might be expected, the template meta-programming features of C++ encouraged a number of compile and run-time dimensional analysis libraries. A search on GitHub reveals over a dozen, and many more can be found on the internet. Most implementations are more or less variations of each other, so we will only look at some representative examples.

Boost
-----

One of the most prominent implementations is [Boost.Units](http://www.boost.org/doc/libs/1_65_0/doc/html/boost_units.html "Official Boost.Units documentation"). It uses compile-time metaprogramming techniques to implement generic and extensible unit systems that do not incur any run-time overhead.

Like most Boost libraries, Boost.Units is very comprehensive, extremely flexible, and tries to cover all posssible use and edge cases. The library does not only check the validity of unit calculations at compile-time, but also allows for compile-time unit calculations according to dimensional analysis rules inside template meta-programs.

The following lines are excerpts from the definition of a simple meter-kilogram-second unit system:

```
struct length_base_dimension : base_dimension { }; struct mass_base_dimension : base_dimension { }; struct time_base_dimension : base_dimension { }; typedef length_base_dimension::dimension_type length_dimension; typedef mass_base_dimension::dimension_type mass_dimension; typedef time_base_dimension::dimension_type time_dimension; typedef derived_dimension::type area_dimension; typedef derived_dimension::type energy_dimension; struct meter_base_unit : base_unit { }; struct kilogram_base_unit : base_unit { }; struct second_base_unit : base_unit { }; typedef make_system< meter_base_unit, kilogram_base_unit, second_base_unit>::type mks_system; typedef unit dimensionless; typedef unit length; typedef unit mass; typedef unit time; BOOST_UNITS_STATIC_CONSTANT(meter, length); BOOST_UNITS_STATIC_CONSTANT(meters, length); BOOST_UNITS_STATIC_CONSTANT(kilogram, mass); BOOST_UNITS_STATIC_CONSTANT(kilograms, mass); BOOST_UNITS_STATIC_CONSTANT(second, time); BOOST_UNITS_STATIC_CONSTANT(seconds, time); template<> struct base_unit_info { static std::string name() { return "meter"; } static std::string symbol() { return "m"; } }; template<> struct base_unit_info { static std::string name() { return "kilogram"; } static std::string symbol() { return "kg"; } }; template<> struct base_unit_info { static std::string name() { return "second"; } static std::string symbol() { return "s"; } };
```

Unit systems defined in this way may then be used as follows:

```
quantity L(2.0 * meters); quantity E = kilograms * pow<2>(L / seconds); quantity > L(std::complex(3.0, 4.0) * meters); quantity > E(kilograms * pow<2>(L / seconds)); const double dimless = (L/L);
```

Note that scientific calculations can be performed out of the box, because the library already includes complete definitions for the SI and CGS unit systems, supports angle and temperature measurements in various units, and provides fine-grained conversions between them.

For a complete description of all features along with numerous examples check out the official documentation.

cpp-measures
------------

Carlo Milanesi's [cpp-measures](https://github.com/carlomilanesi/cpp-measures "cpp-measures on GitHub") is a header-only library for compile-time dimensional analysis using C++ templates. The only pre-defined unit of measure is `radians`. All others must be defined by the user, for example:

```
MEASURES_MAGNITUDE(Length, metres, " m") MEASURES_UNIT(km, Length, " Km", 1000, 0) MEASURES_UNIT(cm, Length, " cm", 0.01, 0)
```

The following example code demonstrates the definition and usage of physical quantities, as well as conversions between units:

```
vect1 a(6); vect1 work = vect2(12, 13) * vect2(3, 5); vect1 t = convert(vect1(90));
```

Support for vector quantities is built into the library and limited to a maximum of three dimensions:

```
point3 b(7, 8, 9);
```

This may seem like a surprising design choice at first, but it enables some interesting calculations. For example, it allows energy to be expressed in relation to vector quantities:

```
vect1 e = vect2(12, 13) * vect2(3, 5);
```

Note that the `*` operator is defined as the dot product here.

Dimentia
--------

[Dimentia](https://www.cs.cmu.edu/~sboucher/dimentia.pdf) is a system that implements a static analysis pass for LLVM in order to perform consistency checks without requiring any input from the programmer. It does so by associating with each program variable a so called _scalar deggree_, which is the sum of exponents of a type's units. These are solely derived from the operations on the variables.

Due to its approach, the system cannot detect semantic errors in isolation, but it can successfully detect confliting usages of variables in larger programs without having to know their intended semantics.

Quantity
--------

Michael Kenniston's [Quantity](http://home.xnet.com/~msk/quantity/quantity.html) is a portable header-only C++ template library for compile-time verification of computations with physical quantities. It includes a `quantity` template type with a fixed set of seven dimensions for modelling the SI system, a comprehensive collection of base and derived units and quantities, arithmetic operations over quantities, SI prefixes, and some support for I/O and unit conversion.

Magnitudes are internally represented as `double` by default, but the behavior can be overriden with a compiler directive. The following code is taken from the library to illustrate how it defines these aspects:

```
typedef dimensions<1, 0, 0, 0, 0, 0, 0> length_d; typedef dimensions<0, 0, 1, 0, 0, 0, 0> time_interval_d; typedef dimensions<1, 0, -1> speed_d; inline Rep milli() { return Rep(1e-3L); } inline Rep kilo() { return Rep(1e+3L); } inline quantity kilogram() { return quantity(detail::permit(Rep(1.0))); } inline quantity gram() { return kilogram() / 1000; } inline quantity newton() { return meter() * kilogram() / square(second()); }
```

The following lines demonstrate the usage of the library:

```
quantity width(1.2f * meter()); quantity height(2.3f * meter()); quantity area(width * height); quantity speed = height / second(); quantity vol = cube(height); double r = width / height; double s = speed * (second() / meter()); quantity e = 42 * kilo() * watt() * hour(); std::cout << e; // "42 m+2 kg s-2"
```

[PhysUnits](https://github.com/martinmoene/PhysUnits-CT-Cpp11) is an adaption of Quantity for C++11. One of the interesting improvements is the added support for user-defined literals, so that quantities can be written more concisely as `1_ns` or `42_km`.

[PhysUnits-CT](https://github.com/martinmoene/PhysUnits-CT) and [PhysUnits-RT](https://github.com/martinmoene/PhysUnits-RT) are versions of PhysUnits for C++98 and for run-time evaluation. The latter increases the number of supported dimensions to 10 and stores them alongside values:

```
quantity F(2.0 * newton()); quantity dx(2.0 * meter()); quantity E(work(F, dx)); std::cout << E; // "4 J"
```

SIunits
-------

Walter E. Brown's _SIunits_ is a template based C++ library for compile-time checking of physical units. The initial version was introduced in the 1998 paper [Introduction to the SI Library of Unit-Based Computation](https://pdfs.semanticscholar.org/8d7a/b4a389a5a8b99594255b4197b11f199a5991.pdf). It has no run-time overhead, includes a large number of pre-defined units, and allows for user defined calibration of base units to accommodate for different precisions/magnitudes.

As a somewhat unique feature, the library also offers five different models for base units to enable calculations from different physical view points, i.e. high-energy, relativistic, or quantum.

The API assumes that values are represented as `double`, but also allows for custom value types via template parameters.

```
Length d1(2.5); // 2.5 meters; same as 2.5 * m Length d2(1.2 * cm); // 1.2 centimeters; recorded as .012 * m Width d3(1.23 * pico_ * meter); // 1.23e-12 * m; Width is a synonym for Length Length d4(d1 + d2); Area a1(d1 * d2);
```

Like many other libraries, SIunits encodes a unit type's dimensions in a 7-tuple that holds the exponent for each dimension. Early implementations used seven integer template parameters, but those were later refined to take a type list of compile-time rational numbers, which permit a broader range of dimensional exponents and cover computations involving roots:

```
Mass<> m = 100 * kilogram; Energy<> e = m * c * c; Velocity<> v = sqrt(e) / sqrt(m);
```

The implementation details can be found in the 2002 paper [Applied Template Metaprogramming in SIunits](https://www.semanticscholar.org/paper/Applied-Template-Metaprogramming-in-SIunits-Brown/3958f4a6dac0fbfed4be87a891df444ed31dd7c3).

D
=

The inclusion of dimensional analysis support in the Phobos standard library [has been discussed](https://forum.dlang.org/thread/io1vgo%241fnc%241@digitalmars.com) for several years and seems to be an ongoing effort. So far there have been only a couple major community projects.

quantities
----------

Nicolas Sicard's [quantities](https://github.com/biozic/quantities) library supports both compile-time and run-time checking of units of measures and includes a comprehensive set of SI units, unit symbols, and prefixes.

Compile-time support is provided via a `Quantity` template that wraps a generic scalar value into a struct whose type contains a vector of dimensions. The dimension vector is used to statically check for dimensional consistency, and it has zero storage and run-time overhead:

```
auto kilometer = kilo(meter); auto distance = 384_400 * kilometer; auto speed = si!"299_792_458 m/s"; Time time = distance / speed; writeln(siFormat!"%.3f s"(time)); // "1.282 s"
```

For run-time support, the library introduces a generic `QVariant` type that stores the vector of dimensions in a member field instead, and inconsistent calculations throw an exception:

```
auto distance = qVariant(384_400 * kilo(meter)); auto speed = parseSI("299_792_458 m/s"); auto time = distance / speed; writeln(siFormat!"%.3f s"(time)); // "1.282 s"
```

To some extent, `Quantity` and `QVariant` can be used together in the same expression. The parser used to read quantities from strings is extensible.

std.units
---------

David Nadlinger's [std.units](http://klickverbot.at/code/units/std_units.html) ([GitHub](https://github.com/klickverbot/phobos/blob/units/std/units.d)) is a library for compile-time checking of units of measurements. It does not define any system of measurement out of the box, but provides a set of mixins for creating user defined base, derived, scaled, and affine units:

```
alias BaseUnit!("Ampere", "A") Ampere; enum ampere = Ampere.init; // or enum ampere = baseUnit!("Ampere", "A"); alias DerivedUnit!( BaseUnitExp!(Ampere, Rational!1), BaseUnitExp!(Second, Rational!1) ) Coulomb; enum coulomb = Coulomb.init; // or enum coulomb = ampere * second; alias ScaledUnit!(Metre, 0.0254, "inch", "in") Inch; // or alias ScaledUnit!(metre, 0.0254, "inch", "in") Inch; // or enum inch = scale!(metre, 0.0254, "inch", "in"); enum celsius = affine!(273.15, "degrees Celsius", "°C")(kelvin);
```

The unit dimensions are encoded into the types. Prefixes are implemented as templates and helper functions that can also be generated automatically:

```
alias PrefixSystem!(10, { return [ Prefix(-3, "milli", "m"), Prefix(3, "kilo", "k")]; }) System; alias prefixTemplate!(-3, System) milli; alias prefixTemplate!(3, System) kilo;
```

The following are usage examples for code with units:

```
enum squareMetre = pow!2(metre); enum celsius = affine!(273.15, "degrees Celsius", "°C")(kelvin); Quantity!(metre, int) x = 6 * metre; auto speed = x / second; assert(l / metre == 6 * dimensionless); auto il = cast(Quantity!(metre, int))x; auto a = pow!2(5 * metre);
```

With the [units-d](https://github.com/nordlow/units-d) library, Per Nordlöw attempted to combine _std.units_ with the expression parsing capabilities of _quantities_.

Eiffel
======

EiffelUnits
-----------

[EiffelUnits](http://se.inf.ethz.ch/old/projects/markus_keller/EiffelUnits.html "EiffelUnits Homepage") is a library for the _Eiffel_ programming language that allows for attaching units to quantities. It includes a set of common scientific units, but can be extended with user defined unit types. The following code snippet declares a constant for gravitational acceleration:

```
Gravity: QUANTITY is -- gravitational acceleration on earth surface once Result := quantity (9.81) * m / (s ^ 2) ensure Result.has_dimension (dim.Acceleration) end
```

`QUANTITY` is a generic type that can hold any combination of unit and quantity. New types of quantities can be created by multiplying and dividing existing base or derived quantities.

`dim.Acceleration` is a predefined instance of the dimension class provided by the library. Each class provides ready to use units, such as `m`, `s` and `kg`. There are also complex derived classes for units with special names, such as `N` for Newtons.

Usage of quantities follows along similar lines:

```
feature {NONE} -- Initialization make (mass_1_: QUANTITY; mass_2_: QUANTITY) is -- Load the machine require is_mass_1: mass_1_.commensurate_with (kg) is_mass_2: mass_2_.commensurate_with (kg) do mass_1 := mass_1_ mass_2 := mass_2_ end feature -- Access mass_1: QUANTITY mass_2: QUANTITY acceleration_1: QUANTITY is -- acceleration of mass 1 do Result := (mass_2 - mass_1) / (mass_1 + mass_2) * Gravity ensure Result.commensurate_with (m * s^-2) end
```

The library performs all semantic validation at run-time. The information needed for this is carried in the instances of quantities. There is no mechanism for checking the correctness of code at compile-time.

Excel
=====

Although technically not programming languages, spreadsheets are similar to declarative functional languages with reactive semantics. They are used as a tool in many financial, engineering and scientifc applications, and therefore the automatic detection of unit errors can be desirable.

XeLda
-----

In [Validating the Unit Correctness of Spreadsheet Programs](https://dl.acm.org/citation.cfm) ([PDF](https://cs.brown.edu/~sk/Publications/Papers/Published/asknf-valid-unit-sprdsht/)) from 2004, Tudor Antoniu et. al. describe a standalone prototype tool for unit checking Excel spreadsheets. Users may annotate spreadsheet cells that contain either values or formulas with a (possibly empty) list of unit names and associated exponents.

For example, an annotation for a force value could be:

```
((kilogram 1) (meter 1) (second -2))
```

The names of units are arbitrary, and their order is not important. The tool parses the cells and annotations in a bottom-up fashion, generates and evaluates unit constraints, and then colors any cells with with consistency errors. It also provides a textual explanation.

![Unit Errors in Excel Spreadsheet](https://gmpreussner.com/user/pages/04.research/dimensional-analysis-in-programming-languages/_excel/xelda.png)

Fortran
=======

Fortran continues to be the predominant programming language of the physical sciences. Surprisingly though, the representation of physical units had not been addressed systematically until more recently.

PHYSUNITS
---------

Grant Petty developed a [software package](http://sleet.aos.wisc.edu/~gpetty/gpetty//physunits.html "Project page for Automated Computation and Consistency Checking of Physical Dimensions and Units in Scientific Program") ([paper](http://onlinelibrary.wiley.com/doi/10.1002/spe.401/abstract "Wiley Online Library: Automated computation and consistency checking of physical dimensions and units in scientific programs")) that adds automated computation and consistency checking of physical dimensions and units to Fortran 90. The implementation has a run-time cost for computations and storage, because dimension information is carried alongside numerical values in additional memory and computed by overloaded operators.

The module implements a number of SI units, which are represented as constants, such as `u_meter`. The following is a valid program that declares velocity, mass and acceleration to compute various energies:

```
v = 10.0*u_meter/u_second m = 5.0*u_kilogram g = 9.807*u_meter/(u_second**2) kinetic_energy = 0.5*m*v**2 potential_energy = m*g total_energy = kinetic_energy + potential_energy
```

Fortress
========

The discontinued language [Fortress](https://en.wikipedia.org/wiki/Fortress_(programming_language) "Wikipedia: Fortress"), a DARPA funded research project started by Sun Microsystems and later slashed by Oracle, had syntax support for dimensional analysis. Of particular interest are the `dim` and `unit` keywords that are used to declare dimensions and units respectively.

The language has largely disappeared from the internet, and most of the original [related publications](https://web.archive.org/web/20080318151108/http://research.sun.com:80/projects/plrg/Publications/ "WaybackMachine: Publications and Fortress Specifications") are no longer available. Some up to date details can be found in the [language specification](http://www.ccs.neu.edu/home/samth/fortress-spec.pdf "PDF: The Fortress Language Specification") and a chapter in the [Encyclopedia of Parallel Computing](https://www.amazon.com/Encyclopedia-Parallel-Computing-Springer-Reference/dp/0387097651/ "Amazon: Encyclopedia of Parallel Computing").

The following code demonstrates the declaration of base and derived dimensions, base and derived units with and without scaling, as well as their use in program statements:

```
dim Length default meter (* base dimensions *) dim Time default second dim Velocity = Length/Time (* derived dimension *) unit meter m: Length (* base units *) unit second s: Time unit joule J: Energy = newton meter (* derived unit without scaling *) unit centimeter cm: Length = 10⁻² meter (* derived unit with scaling *) d: RR64 Length = 2 m_ t: RR64 Time = 4 s_ v:= d / t (* 0.5 m_/s_ *)
```

Frink
=====

Another language with built-in support is [Frink](https://frinklang.org/ "Frink Homepage"), although it is more of a tool for physics calculations than a general purpose programming language. Units of measure and unit conversion are a major pillar of the language's design and largely driven by a [data file](https://frinklang.org/frinkdata/units.txt "Frink Data File") consisting of predefined units, prefixes, constants and relationships.

The following code demonstrates the declaration and usage of variables:

```
mass = 2 kg gravity = 9.81 m/s^2 force = mass * gravity // 19.62 kg m/s^2 force2 = 19.62 newton // same as 'force'
```

The author has put considerable effort into analyzing the pitfalls and ambiguities of representing physical dimensions in computer programs using standard mathematical notation and orthography. The language also has some other interesting features that make it worth a look.

F#
==

The first general purpose (and hitherto only mainstream) programming language with built-in support for static checking and inference of units of measure is F#. Andrew Kennedy's blog has a [brief overview](https://blogs.msdn.microsoft.com/andrewkennedy/2008/08/29/units-of-measure-in-f-part-one-introducing-units/ "Units of Measure in F#") ([Part 2](https://blogs.msdn.microsoft.com/andrewkennedy/2008/09/02/units-of-measure-in-f-part-two-unit-conversions/), [Part 3](https://blogs.msdn.microsoft.com/andrewkennedy/2008/09/04/units-of-measure-in-f-part-three-generic-units/)) of that particular feature. You might also want to read his [related paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.538.964&rep=rep1&type=pdf "PDF: Types for Units-of-Measure: Theory and Practice") and [dissertation](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.93.807&rep=rep1&type=pdf "PDF: Programming Languages and Dimensions") for some more theoretical background.

The language provides a `Measure` attribute that enables the declaration of measurement types, which can then be used to annotate numerical values using an angle bracket notation. Derived units are type aliases for algebraic combinations of base units. The language also supports unit conversions, dimensionless quantities and generic functions.

The following code declares base and derived unit types and demonstrates their semantic equivalency when used in program statements:

```
[] type kg // declaration of base unit types [] type m [] type s let mass = 2.0 let gravity = 9.81 let force = mass * gravity // 19.62 [] type N = kg m/s^2 // declaration of derived unit type let force2 = 19.62 // same as 'force'
```

Haskell
=======

Haskell's strong static typing and widespread use in the scientific community make it a prime candidate for researching dimensional analysis in programming languages. A number of different solutions exist, and the most popular ones are presented below.

Boyer
-----

Stephan Boyer presented a [simple approach](https://www.stephanboyer.com/post/131/type-safe-dimensional-analysis-in-haskell "Stephan Boyer's blog") using function spaces. It has a few limitations, such as an awkward construct/destruct syntax and a need to arrange arguments of unit operations in the right order.

```
type Length = BaseQuantity Meter tableWidth :: Length tableWidth = construct 1.5 tableHeight :: Length tableHeight = construct 2.5 tableArea :: Area tableArea = tableWidth .*. tableHeight
```

dimensional
-----------

The [dimensional](https://github.com/bjornbm/dimensional/ "dimensional on GitHub") package ([Hackage](https://hackage.haskell.org/package/dimensional "dimensional on Hackage")) is a recent dimensional analysis implementation that has a slightly more familiar syntax based on _Closed Type Families_ and _Data Kinds_ for dimension tracking.

```
leg :: Length Double leg = 1 *~ mile speeds :: [Velocity Double] speeds = [60, 50, 40, 30] *~~ (kilo meter / hour)
```

physics
-------

The [physics](http://haskell-libs.cvs.sourceforge.net/haskell-libs/libs/physics/ "SourceForge: haskell-libs physics") Haskell package is the oldest implementation of dimensional analysis in Haskell that I could find. It is fairly simple and limited.

```
test1 :: Velocity -> Time -> Length test1 m n = mult m n test2 :: Length -> Time -> Velocity test2 m n = divide m n
```

units
-----

The [units](https://github.com/goldfirere/units "units on GitHub") package ([Hackage](https://hackage.haskell.org/package/units "units on Hackage")) is a more sophisticated solution that provides a fully extensible embedded type system with support for independent notions of dimensions and unit, inter-convertible units of the same dimension, unit-polymorphic programs, and unit prefixes. It also includes definitions for SI units.

```
-- dimension definition data LengthDim = LengthDim instance Dimension LengthDim -- derived dimension type VelocityDim = LengthDim :/ TimeDim -- unit definition data Meter = Meter instance Unit Meter where type BaseUnit Meter = Canonical type DimOfUnit Meter = LengthDim -- value type definition type Length = MkQu_DLN LengthDim LCSU Double -- values and prefixes len :: Length len = 3 % Meter longLen :: Length longLen = 150 % kilo Meter -- value computations vel = (3 % Meter) |/| (2 % Second)
```

uom-plugin
----------

A completely different implementation approach can be found in Adam Gundry's [uom-plugin](https://github.com/adamgundry/uom-plugin "uom-plugin on GitHub") package ([Hackage](https://hackage.haskell.org/package/uom-plugin "uom-plugin on Hackage")). It uses GHC's facility for type checker plug-ins to add support for units of measure. The [accompanying paper](http://adam.gundry.co.uk/pub/typechecker-plugins/ "PDF: A Typechecker Plugin for Units of Measure") describes the ideas behind it in more detail. There is also a brief [tutorial](https://hackage.haskell.org/package/uom-plugin-0.2.0.1/docs/Data-UnitsOfMeasure-Tutorial.html "uom-plugin tutorial") that explains the basics.

```
gravityOnEarth :: Quantity Double [u| m/s^2 |] gravityOnEarth = [u| 9.808 m/(s*s) |]
```

Java
====

MetaGen
-------

In 2004, Eric Allen et. all presented a very comprehensive implementation of [Object-oriented units of measurement](https://dl.acm.org/citation.cfm?id=1029008) for Java. At the heart of it lies the observation that dimensions and units have a dual nature in being both types (to statically check expressions) and values (can be multiplied together). They conclude that this necessitates support for generic metaclasses, which they introduce via custom language extensions.

It is my understanding that the abstraction mechanisms available in Java today are still insufficient to model all desired aspects as proposed without introducing extensions, and it is therefore not an off-the-shelf solution for the general Java programmer. Nevertheless, the paper is worth a read as it covers basic terminology, design challenges and constraints, uncommon edge cases, and a detailed analysis of the underlying problems.

The paper's summary outlines that their solution allows for parametric and inheritance polymorphism with respect to both dimension and unit types, integration of encapsulated measurement systems, dynamic conversion factors, declarations of scales (including nonlinear scales) with defined zeros, and nonconstant exponents on dimension types.

In classical Java style, this results in many layers of abstractions, the details of which cannot be explained in a couple paragraphs. The interested reader is therefore referred to the original paper. To illustrate just one aspect of metaclasses, consider the implementation of measurements.

A metaclass `Dimension` is introduced to declare instance classes for specific dimensions, which may also have static member functions:

```
abstract class Dimension { abstract String shortName(); } Dimension Length { static String shortName() { return "L"; } } Dimension Time { static String shortName() { return "T"; } }
```

Note that `Length` and `Time` are also classes. Units are classes that extend dimensions, which means that every unit is associated with its own type:

```
class* Unit extends D { ... } Unit Minute { ... } Unit Foot { ... } Unit Mile { ... }
```

Measurements are classes that are tied to units:

```
class Measurement U> extends D { private final Real _magnitude; }
```

We can now declare symbols that can be interpreted as both an instance (object) of measurements and a class instance:

```
Measurement CircumferenceOfEarth { static { container(24889); } }
```

As a result, `_magnitude` can be either a field on an object, or a static field on a class. In their actual implementation, magnitudes are of generic types (via another class called `Unity`) and not limited to real numbers.

Lisp
====

Cunis
-----

In [A package for handling units of measure in Lisp](https://dl.acm.org/citation.cfm) ([PDF](http://3e8.org/pub/scheme/doc/lisp-pointers/v5i2/p21-cunis.pdf)) from 1992, Roman Cunis introduces a _Common Lisp_ package for representing and checking units of measurement at run-time. The paper does not provide any code for implementation and usage examples, but contains some interesting ideas.

Instead of using vectors to represent unit dimensions, it associates base units with prime numbers that can be multiplied together into ratios to represent compound units. The scaling of units is done at input time, so that all quantities are internally stored in base units.

It also introduces a compact syntax for defining measures and units:

```
(defmeasure speed ; name of measure "m/s" ; base unit :units ("km/h" ; implicit unit definition ("mph" 1.6km/h) ; explicit unit definition ) : output-format (:unit "mph") ; all speeds printed scaled to mph ) 
```

Novak
-----

In [Conversion of units of measurement](https://www.cs.utexas.edu/users/novak/units95.pdf) from 1997, Gordon S. Novak Jr. presents algorithms and their implementation for representing, converting, normalizing, and automatic checking of units in _GLisp_, which is an extension of Lisp with structural abstractions.

Novak distinguishes between simple and composite units. Simple units include base units (`kilogram`), named units that can be defined in terms of other units (`horsepower`), and SI prefixes for scaling (`nano`). They are associated with a numeric conversion factor to base units.

Composite units are products or quotients of simple units:

```
(* 60 (/ mile hour)) ; 60 mph (/ (* 2000 kilo calorie) day) ; 2000 kcal/day
```

Simple and composite units along with their scaling factors and aliases can be defined as follows:

```
(defsimpleunits `length `((meter 1.0 (m meters))) (foot 0.3048 (ft feet)) (angstrom 1.0e-10 (a angstrom))) (defderivedunits `force `((newton (/ (* kilogram meter) (* second second)) (nt netwons)) (pound-force (/ (* slug foot) (* second second)) (lbf))))
```

The package provides aliases for common simple and composite units, such as `kg`, `mph`, and `tablespoons`. Quantities for physical constants are defined by packaging them together:

```
`(q 2.997 (/ meter second)) ; 2.997 m/s
```

Units can be converted into each other:

```
(glconvertunit 'kilogram 'lb) ; 1 kg = 2.20462 lb (glconvertunit '(/ (* 2000 kilo calorie) day) 'watt) ; 2000 kcal/day = 96.85185 W
```

Units can also be simplified, so that they have at most one `/` at the top, or use common names:

```
(glsimplifyunit `(/ meter foot)) ; 3.280839895013123 (glsimplifyunit `(/ joule watt)) ; SECOND (glsimplifyunit `(/ joule horsepower)) ; (* 0.001341022 SECOND) (glsimplifyunit `(/ (* kilogram meter) (* second second))) ; NEWTON
```

And, of course, the whole point is to be able to use them in functions:

```
(gldefun test (speed\:(units real (/ (* atto parsec) (* micro fortnight)))) (if (speed > '(q 55 mph)) (print "speeding")))
```

The package's dimensional analysis facilities combine the seven SI base units and a unit type for monetary values into an 8-vector of integers. Products and quotients of units are calculated as sums and differences of vectors. The paper describes a bit packing scheme to store dimensions in a single 32-bit integer, and it discusses support for generic quantities.

The code can be downloaded from [Novak's website](https://www.cs.utexas.edu/users/novak/units.html), which also has an [online demo](https://www.cs.utexas.edu/users/novak/cgi/unitsdemoty.cgi) for testing unit conversions in a web browser.

Nemerle
=======

Nemerle is a high-level multi-paradigm general purpose programming language for the .NET common language infrastructure with a C# like syntax and powerful metaprogramming support.

Oyster Units
------------

Andriy Kozachuk wrote a small implementation as a learning excercise for converting template code from C++ to Nemerle. It is documented in a [forum post](http://rsdn.org/forum/src/1823225.flat#1823225) and uses a combination of classes, attributes and compile-time macros to add support for units. The assembly also contains declarations for common base and derived CGS and SI units.

```
def m1 = Cgs.Mass(1); // 1 gram def l1 = Cgs.Length(100); // 100 centimeters def l2 = Si.Length(l1); // auto conversion to 1 meter def t1 = Cgs.Time(1); // 1 second def f3 : Si.Force = m1 * l2 / (t1 * t1);
```

The subsequent forum discussion contains a number of improvements and fixes. The latest version appears to be [Oyster.Units.0.05](http://rsdn.org/File/27948/Oyster.Units.0.05.zip).

Nim
===

Nim is a relatively new programming language and as such did not yet have as much exposure as many of the other languages discussed here. Nevertheless, it has some very interesting capabilities, such as powerful metaprogramming facilities that allow for manipulating the abstract syntax tree at compile time, and generic types where parameters can have algebraic dependencies.

Existing units of measure implementations are still very scarce and do not use the language's full potential. The [dimrod](https://github.com/ClementJnc/dimrod) module was one of the earliest attempts that seems to have been abandoned a few years ago.

metric
------

A recent and more advanced implementation is Michael Jendrusch's [metric](https://github.com/mjendrusch/metric) package, which ships with an extensible set of SI units, prefixes, and natural constants. It uses a combination of _concepts_ and macros to generate unit types at compile-time.

Dimensions are encoded as static tuples of arbitrary length. New base units and prefixes can be declared and implemented as follows:

```
type Length* = object of BaseDimension template `$`*(x: typedesc[Length]): string = "m" template centi*(x: auto): auto = 1e-2 * x const meter = Metric[Length, float](val: 1.0) cm {. used .} = centi m inch = 2.54 * cm
```

Such units can then be used in code and will be verified at compile-time:

```
withUnits: var v0 = 40.0 * mile / hour echo "v0 in miles per hour: ", fmt "{v0 as mile / hour} [mph]" echo "v0 in decimeters per fortnight: ", fmt "{v0 as dm / (2.0 * week)} [dm / fortnight]" echo "v0 in SI units: ", v0
```

Note that `fmt` evaluates an expression to format the output string, and `as` is a template function for converting unit types.

Pascal
======

Dimensions cannot be easily expressed in Pascal's type system, but there have been a number of proposals for physical units support in the late 70's and mid 80's, most notably by [Gehani](https://dl.acm.org/citation.cfm), [Männer](https://dl.acm.org/citation.cfm), [Dreiheller](https://dl.acm.org/citation.cfm), and [Agrawal](https://dl.acm.org/citation.cfm). Some of these suggestions were later implemented by others.

Baldwin
-------

Geoff Baldwin's paper [Implementation of Physical Units](https://dl.acm.org/citation.cfm) describes an implementation of strong typing with physical units in a minimally extended Pascal compiler. It is not extensible and limited to a small number of units for a specific electrical use case.

Like many other implementations, Baldwin internally represents units as dimnensionality vectors. He modified the lexer to recognize certain expressions, convert them into appropriate values and synthesize the corresponding dimensionalities. For example, the expression `1.2mV` is interpreted and stored in the symbol table as `1.2e-3` of type `VOLTAGE`.

Vector Pascal
-------------

[Vector Pascal](https://en.wikipedia.org/wiki/Vector_Pascal "Vector Pascal on Wikipedia") is an extension of a Pascal compiler with focus on SIMD algorithms. Its type system has built-in support for dimensional analysis. The implementation details are described in Paul Cockshott's [paper](https://pdfs.semanticscholar.org/2633/cc6f3adf86127789e477068c873b970b444e.pdf).

The following example code defines the basis space of a dimensioned type and declares a number of base and derived unit types:

```
type kms = (mass, distance, time); meter = real of distance; kilo = real of mass; second = real of time; newton = real of mass * distance * time POW -2; meterpersecond = real of distance * time POW -1;
```

Perl
====

Data::Dimensions
----------------

The [Data::Dimensions](http://search.cpan.org/~ajgough/Data-Dimensions-0.04/lib/Data/Dimensions.pm) module implements physical values using strongly typed values. Quantities are defined by initializing a `Dimensions` object with dimensionality exponents and an optional initial value:

```
$distance = Data::Dimensions->new( {meter => 1 } ); # 0 m $time = units( {hour => 1}, 2 ); # 2 hours $speed = units( {miles => 1, hour => -1}, 70 ); # 70 mph
```

Once defined, variables retain their initial units, so that subsequent values can be assigned without specifying unit names. Units of expressions are derived automatically via operator overloading. Operations with untyped values are assumed to have the same unit as the other operand:

```
set $speed = 60; # 60 mph set $distance = $speed * $time; # 120 miles set $newspeed = $speed + 10; # 70 mph
```

The module provides a collection of SI and other common units and prefixes, and it also allows for user-defined units.

Math::Units
-----------

[Math::Units](http://search.cpan.org/~jettero/Math-Units-PhysicalValue-1.0009/lib/Math/Units/PhysicalValue.pod) focuses on automatic conversion of values with compatible units. It is still in an early stage, but already supports prefixes, reductions, conversion factors, along with some optimizations to speed things up at run-time.

```
convert(5, 'mm', 'in') # 0.19685 convert(4500, 'rpm', 'Hz') # 75
```

The [Math::Units::PhysicalValue](http://search.cpan.org/~jettero/Math-Units-PhysicalValue-1.0009/lib/Math/Units/PhysicalValue.pod) module was built on top of _Math::Units_ to provide an object-oriented interface for unit calculations. Internally, it splits and stores value strings separately as an array and evaluates them using overloaded operators.

```
$height = new Math::Units::PhysicalValue "10,000 ft"; $duration = "43 s"; $speed = $height / $duration; $weight = "180 lbs"; $momentum = ($weight * $speed) + "0 kg*m/s"; print "$momentum\n"; # "5,787.42 kg*m/s" print ($speed + "0 miles/hour"), "\n" # "158.56 miles/hour"
```

Physics::Unit
-------------

The [Physics::Unit](http://search.cpan.org/~klortho/Physics-Unit-0.04/lib/Physics/Unit.pm) module is interesting, because it has a couple unusual characteristics. First, it introduces a `Unit` type that is not only used to represent base and derived units, but also unit prefixes and conversion factors. It combines the conversion factor, a dimensionality vector of ten integers, and an optional list of unit name in a single structure. A unit prefix would be represented as a dimensionless unit with a single name.

Named "units", such as `kilo`, `foot`, or `mg` are constants that do not change at run-time in order to guarantee that their usage in algorithms and derived units remains consistent. For unit values that change at run-time, such as variables or intermediate results, the module uses unnamed units, also called _anonymous units_.

Then, the module defines a set of operators, some of which are aliased. It also includes a whitespace operator that allows for the concatenation of prefixes, conversion factors, and units in different ways. In particular, whitespace between two unit names is considered a multiplication, but concatenation without whitespace is also allowed.

For example, the following notations are all equivalent:

```
megaparsec mega parsec kilo kilo parsec kilo**2 parsec square kilo parsec
```

Obviously, this notation allows (if not encourages) the combination of unit prefixes, which is actually prohibited in the SI system. Precedence rules for the various operators are rather complicated and must be studied carefully. For example, the unit for acceleration, m/s2, can be expressed as `meters / sec sec`, but not `meters / sec*sec` (the seconds cancel out).

The module includes a comprehensive set of SI and other common units and prefixes, but also allows for the definition of arbitrary custom unit types of up to ten dimensions. The following are excerpts from its implementation to demonstrate the syntax for defining new base units, prefixes, derived units, and associated data types:

```
InitBaseUnit ( 'Distance' => ['meter', 'm', 'meters'], 'Mass' => ['gram', 'gm', 'grams'], 'Time' => ['second', 's', 'sec', 'secs', 'seconds'], 'Current' => ['ampere', 'amp', 'amps', 'amperes'] ); InitPrefix ( 'kilo', 1e3, 'milli', 1e-3, 'mebi', 2^20, 'semi', 0.5 ); InitUnit ( ['unity', 'one', 'ones',], '1', ['hundredth',], '0.01', ['percent', '%',], '0.01', ['radian', 'radians',], '1', ['degree', 'deg', 'degrees',], 'pi radians / 180', ['foot', 'ft', 'feet',], '.3048 m', ['inch', 'in', 'inches',], 'ft/12', ['mg',], 'milligram', ['tesla', 'teslas'], 'kg / amp sec^2' ); InitTypes ( 'Dimensionless' => 'unity', 'Magnetic_field' => 'tesla', 'Acceleration' => 'm/s^2' );
```

Python
======

There exist a substantial number of packages for handling units in Python. Dr. Dobb's online magazine has an [overview](http://www.drdobbs.com/jvm/quantities-and-units-in-python/240161101) of the three most prominent ones. A selection of other packages is listed on the homepage of [natu](http://kdavies4.github.io/natu/seealso.html), which is not discussed here. Most of these have a similar API and feature set, so I will only cover a few.

Biggs
-----

In [A Design for Dimensional Analysis in Robotics](https://www.researchgate.net/publication/228991349_A_design_for_dimensional_analysis_in_robotics) from 2005, Geoffrey Biggs presents the design requirements and custom Python interpreter called _RADAR_ for use in dimensional analysis in robot software.

Biggs chose to attach unit information to data values, so that they are available at run-time and help verify computations on input operations. The following code demonstrates the definition of dimensions and units:

```
dimension.DefineDimension (’fasterthanlight’) dimension.DefineUnit ('fasterthanlight’, ’warp’, UnitPrec_Floating, 1.0, UnitRange_Exclude, 0, UnitRange_Include, 9.9) 
```

The module includes definitions for commonly used units and also supports dimensionless types. Units can be added to scalar values by concatenating them with the `~` character, and derived units are specified via the `*`, `/` and `^` operators as follows:

```
distance = 10~m gravity = 9.81~m/s^2 r = (distance * 10) / 5 - 1~m speed = (r / 1~s) / 10
```

numericalunits
--------------

[numericalunits](https://pypi.org/project/numericalunits/) implements units and dimensional analysis with zero run-time overhead in a non-intrusive way, and it works with any numerical calculation routine, including _numpy_ and _scipy_. Quantities are internally stored as regular integer or floating-point numbers, and dimensions are encoded as multiplicative factors.

Since no type information is attached to quantities, the package is of somewhat limited use. In particular, there is no way to see what unit a particular quantity is in, and semantic consistency is detected in a rather obscure way that involves running the same program twice and checking whether the output is identical.

```
from numericalunits import mL, nm, V, cm, e, me, m, s x = 5 * mL print(x / nm**3) # 5e21 (cubic nanometers) Efield = 1e5 * (V / cm) force = e * Efield # elementary charge accel = force / me print(accel / (m / s**2)) # 1.7588e18
```

Pint
----

[Pint](https://pypi.org/project/Pint/) includes many physical units, prefixes and constants, and it has no dependencies on other packages. Extensible unit definitions are loaded from text files. It also includes parsing of units and quantities, as well as string formatting routines for pretty printing and LaTeX.

```
import pint ureg = pint.UnitRegistry() x = 24.0 * ureg.meter # print(x.magnitude) # 24.0 print(x.units) # meter print(x.dimensionality) # [length] t = 8.0 * ureg.second speed = x / t print(speed) # 3.0 meter / second speed.ito(ureg.inch / ureg.minute) print(speed) # 7086.614173228345 inch / minute user_input = '2.54 * centimeter to inch' src, dst = user_input.split(' to ') q = Q_(src).to(dst) # 
```

ScientificPython
----------------

Konrad Hinsen's [ScientificPython](https://bitbucket.org/khinsen/scientificpython/) is a collection of modules for scientific applications that also provides a data type for representing [physical quantities](https://bitbucket.org/khinsen/scientificpython/src/7fef5df489b0588899a6582a3c62ccde447f8ece/Scientific/Physics/PhysicalQuantities.py) with units.

```
d1 = PhysicalQuantity('10 m') d2 = PhysicalQuantity('10 km') total = d1 + d2 # PhysicalQuantity(10010.0,'m') total.convertToUnit('km') total.getValue() # 10.01 e = PhysicalQuantity('2.7 Hartree*Nav') e.convertToUnit('kcal/mol') # PhysicalQuantity(1694.2757596034764,'kcal/mol') str(e.inBaseUnits()) # '7088849.77818 kg*m**2/s**2/mol'
```

The _PhysicalQuantities_ module has dependencies on other _ScientificPython_ modules. Hans Petter Langtangen isolated the relevant bits into a [standalone module](https://github.com/hplgit/physical-quantities), and Georg Brandl ported it [for use in IPython](https://bitbucket.org/birkenfeld/ipython-physics) notebooks.

units
-----

[units](https://pypi.org/project/units/) is yet another Python package for quantities and units that strictly disallows invalid operations. What makes it slightly different from other packages is the way in which instances of units are defined. Newly created units are automatically incompatible with other units, but can be combined via multiplication and division.

```
from units import unit metre = unit('m') second = unit('s') print(metre(10) / second(2)) # 5.00 m / s print(metre(10) ** 3) # 1000.00 m * m * m
```

The package also contains an optional patch that turns the Python interpreter into a unit-enhanced version to enable a more compact syntax:

```
print(2cm / 0.5 s) # 4.0 cm / s
```

Rust
====

Rust is a relatively new programming language that has already gathered a large following due to being sponsored by Mozilla. Several solutions for dimensional analysis exist, some of which are described below.

dimensioned
-----------

[dimensioned](https://github.com/paholg/dimensioned "dimensioned on GitHub") ([crate](https://crates.io/crates/dimensioned/ "dimensioned on crates.io")) is a library for compile-time dimensional analysis with zero run-time cost designed for ease of use (but not necessarily readability). It ships with a somewhat incomplete collection of pre-defined SI, CGS, FPS, and MKS units, and two sets of prefixes, one for 32-bit and one for 64-bit values.

```
let length = 6.0 * dim::si::M; let time = 3.0 * dim::si::S; let vel = 2.0 * dim::si::M/dim::si::S; let vel2 = length / time; fn speed(dist: dim::si::Meter, time: dim::si::Second) -> dim::si::MeterPerSecond { dist / time }
```

Custom unit types can be created with a `make_units!` macro, which is also used to define the built-in systems:

```
make_units! { MS; ONE: Unitless; base { M: Meter, "m", Length; S: Second, "s", Time; } derived { MPS: MeterPerSecond = (Meter / Second), Velocity; HZ: Hertz = (Unitless / Second), Frequency; M3: Meter3 = (Meter * Meter * Meter), Volume; M5: Meter5 = (Meter3 * Meter * Meter); } constants { FT: Meter = 0.3048; CM: Meter = CENTI * M.value_unsafe; MIN: Second = 60.0; HR: Second = 60.0 * MIN.value_unsafe; PI: Unitless = consts::PI; } fmt = true; }
```

runits
------

[runits](https://github.com/jesse99/runits "runits on GitHub") stores unit types and values in a struct and performs validation at run-time. It provides a `Unit` enumeration with constructors for SI and common unit types, a `Compound` constructor for creating derived units, a `Value` struct that packages unit and value, a set of methods on those types, and some helper functions.

```
let speed = from_units(30.0, Mile/Hour); let delta = from_units(2.0, Meter/Second); let sum = speed + delta;
```

simple\_units
-------------

Another compile-time unit system for Rust is [simple\_units](https://github.com/willi-kappler/simple_units "simple_units on GitHub"). It consists of a small set of macros to define unit types, methods on those types, and conversion functions. One interesting aspect of it is that all units, even those for the same dimension, such as meter and foot are distinct types and require conversion functions.

```
let length = Meter(20.72); let time = Second(12.39); let velocity = length / time; let duration = Second(35.0); let distance: Meter = velocity * duration; let distance_in_foot = Foot::from(distance);
```

uom
---

One compile-time library with a richer feature set is [uom](https://github.com/iliekturtles/uom "uom on GitHub") ([crate](https://crates.io/crates/uom "uom on crates.io")). The library normalizes all quantities to base units, and the values can be stored in a number of underlying storage types. It includes SI units and supports automatic conversion between units.

```
let length = Length::new::(5.0); let time = Time::new::(15.0); let vel = Velocity::new::(3.0); let vel2 = length / time;
```

User defined unit systems can be defined using the included macros:

```
#[macro_use] mod length { quantity! { quantity: Length; "length"; dimension: Q; units { @meter: 1.0E0; "m", "meter", "meters"; @foot: 3.048E-1; "ft", "foot", "feet"; } } } #[macro_use] mod mass { quantity! { quantity: Mass; "mass"; dimension: Q; units { @kilogram: 1.0; "kg", "kilogram", "kilograms"; } } } #[macro_use] mod time { quantity! { quantity: Time; "time"; dimension: Q; units { @second: 1.0; "s", "second", "seconds"; } } } system! { quantities: Q { length: meter, L; mass: kilogram, M; time: second, T; } units: U { mod length::Length, mod mass::Mass, mod time::Time, } }
```

Scala
=====

Libra
-----

[Libra](https://to-ithaca.github.io/libra/) is a dimensional analysis library based on typelevel induction for compile-time verification of units of measure. Zainab Ali wrote a detailed [blog post](https://typelevel.org/blog/2017/06/13/libra.html) explaining the rationale, implementation and usage of it, so I won't go into too much detail here.

Dimensions are represented as [heterogenous type lists](http://enear.github.io/2016/04/05/bits-shapeless-1-hlists/) with singleton types as exponents on which operations can be performed at run-time in order to derive new unit types that arise during calculations with quantities:

```
type LightYearSeconds = LightYear :: Second :: HNil type MetresPerSecond = FieldType[Metre, 1] :: FieldType[Second, -1] :: HNil
```

User code generally doesn't have to deal with this verbose notation as the library provides a set of extension methods for common units that can be used directly on scalar values:

```
val distance = 3.0.m val time = 2.0.s val speed = distance / time
```

Squants
-------

[Squants](https://github.com/typelevel/squants) is a framework of data types and a domain specific language for type and thread-safe compile-time dimensional analysis. It uses regular classes to represent unit types and hence requires boxing and unboxing of values with the associated run-time overhead.

```
import squants.energy.{Gigawatts, Kilowatts, Power} import squants.time.{Hours, Days} val ratio = Days(1) / Hours(3) val load = Kilowatts(1.2) val time = Hours(2) val energyUsed = load * time val load2 = load in Gigawatts val s: String = load toString Kilowatts
```

Via implicit conversions, the library provides a DSL that is more akin to scientific notation for simple expressions:

```
val load1 = 100 kW val load2 = 100 megawatts val freq = 60 / second val time = 3.hours + 45.minutes // dots required here
```

Ranges are supported out of the box:

```
val range1 = 1000.kW to 5000.kW val range2 = 5000.kW plusOrMinus 1000.kW val range2 = 5000.kW +- 1000.kW
```

There is also built-in support for vector quantities, string formatting, and unit simplification. In total, the library currently implements over 250 units for SI, monetary and information quantities.

Internally, it appears that all the common operations between different unit types, as well as unit conversions are hard-coded. There are some special traits to handle time derivaties, specifically, in a more convenient way.

Supersquants
------------

In Scala, [tagged types](http://dcapwell.github.io/scala-tour/Tag%20Types.html "Scala Tour: Tag Types") are a technique for creating distinct value types that have the same underlying representation without having to box and unbox them with reference types acting as wrappers. This is usually accomplished by storing tags in the type parameters of Scala traits. The trick is that this extra type information is used only at compile-time. At run-time, the tagged values are equivalent to regular values.

Mikhail Savinov's [supersquant](https://github.com/rudogma/scala-superquants "GitHub: scala-supertagged") uses a custom implementation of tagged types on top of the [supertagged](https://github.com/Rudogma/scala-supertagged "GitHub: scala-supertagged") library in order to implement unit types:

```
trait DoubleLengthTypesTrait { object Length extends TaggedType[Double] type Length[T] = (Double with Tag[Double, Length.Tag]) @@ T object Meters extends OverTagged(Length) type Meters = Meters.Type object Kilometers extends OverTagged(Length) type Kilometers = Kilometers.Type }
```

Units are defined in a shared trait:

```
trait LengthForRawOpsTrait[Raw] extends Any { def meters: Meters = safecasted def km: Kilometers = safecasted }
```

Together, these can then be used to define quantities:

```
val meters:Meters = 5.meters // or val meters:Meters = Meters @@ (Length @@ 5L)
```

The exponents of unit dimensions are also stored as tags in traits. This makes for a very verbose syntax in user code, but it can be somewhat simplified using by predefined aliases:

```
type Acceleration = Complex[Long, Pow[Long, Meters, PowPlus, Nat._1] :: Pow[Long, Seconds, PowMinus, Nat._2] :: HNil] // or type Acceleration = Complex[Long, Single[Meters] :: Squared[Seconds] :: HNil] val squaredSeconds:Pow[Long, Seconds, PowPlus, Nat._1] = 5L.as[Pow[Long, Seconds, PowPlus, Nat._1]] // or val squaredSeconds:Squared[Seconds] = 5L.as[Squared[Seconds]]
```

Quantities can also be converted and formatted for printing:

```
val mg:Milligrams = 5.kg in Grams // 5000 Milligrams 10.kg.pretty // "10 kg" 11123456789L.mg.pretty[Tonnes :: Kilograms :: Grams :: Milligrams :: HNil] // "11 t 123 kg 456 g 789 mg"
```

Actual operations on unit types are performed and verified via operations on traits and yield the expected behavior:

```
val metersXseconds = 5.meters ** 5.seconds val speed3:Speed = 5.meters divide (5.seconds ** 5.seconds) val plainMeters:Meters = speed3 ** (5.seconds ** 5.seconds) val plainLong = speed3 ** (5.seconds ** 5.seconds divide 5.meters)
```

The library currently provides unit types only for length, mass, time, and information units, along with a set of common prefixes. User defined unit types can be added by following the same patterns though. The value specific traits must be implemented separately for each underlying type (the library includes support for 64-bit signed integer and floating-point values).

Summary
=======

I do not wish to attempt a classification of the various implementations described in this article, but I'd like to point out some of the major differences between them. Each of the design decisions have advantages and disadvantages, and their value often depends on the particular use case.

Compile-time vs. Run-time
-------------------------

Catching semantic errors in program code as early as possible is a very desirable feature, which is why most authors opt for compile-time checking of unit types. Compiler assisted dimensional analysis also has the major advantage that it usually does not incur any run-time overhead.

Run-time verification requires extra storage and logic, but it is by no means limited to those programming languages that do not provide adequate syntax support. There are valid use cases that cannot be solved with compile-time systems, for example, if the units are not known until run-time, or if the unit system must be configurable by the user.

Pre-processor vs. Type System
-----------------------------

For dimensional analysis at compile-time most authors will leverage the programming language's type system as it turns the problem of verifying unit semantics into the much simpler problem of verifying program syntax. It therefore pushes the burden of verification to the compiler, which is already implemented. In some cases, it may be necessary to make minor modifications to the parser or compiler in order to support the desired syntax, but this still requires considerable less effort than writing dimensional analysis tools from scratch.

When programming languages are not expressive enough, pre-processing tools that convert annotated source code into compilable source code seem to be a natural choice. However, these shouldn't be dismissed as a last resort to work around the limitations of the language, because standalone tools that deduce unit dimensions automatically can be a great help in analyzing code that has not been annotated at all. This is extremely useful for verifying existing programs without having to refactor them.

Automatic vs. Assisted Unit Inference
-------------------------------------

Opinions differ on how much the source code should be annotated in order to support dimensional analysis. Some argue that the entire process should be as transparent as possible and not require any annotations at all. Many libraries, regardless of whether they use the type system or annotations, are very verbose and put a huge burden on the programmer. This is seen as undesirable. The main downside of fully automated verification is that it requires a certain amount of context to construct a system of constraints, and therefore it cannot capture all use cases.

At the other end of the spectrum, some authors note that annotating source code with units can actually increase the readability, comprehensibility, and maintainability of programs as it better describes the intent of the computations. It seems that, depending on the use case, a balance must be struck between the two approaches.

Integer vs. Rational Unit Exponents
-----------------------------------

The vast majority of libraries and tools for dimensional analysis assume integral unit exponents, which cover most use cases and are easier to implement. However, scientific computations exist that involve the roots of units, particularly in high-energy physics. The added complexity for supporting rational unit exponents allows for computations that could not be expressed otherwise and may therefore be worth the extra effort.

Pre-defined vs. Extensible vs. Data-driven Units
------------------------------------------------

The lack of abstraction capabilities in early (and even some modern) programming languages can make the development of extensible unit of measurement systems difficult or impossible, while more powerful type systems allow for units to be defined or extended by the user. Depending on the use case, a fixed set of units, such as SI is not necessarily a limitation though. In fact, they can lead to simpler and more efficient implementations, especially in those designed for run-time.

For compile-time systems with adequate compiler support there is generally no reason to not provide a generic and extensible API as they will most likely be built on top of generic programming features anyway.

Some frameworks support the definition of units in separate text files, so that they can be modified after the program has been compiled.

Coherent vs. Incoherent Unit Storage
------------------------------------

Each physical dimension may have multiple units that require conversion functions between them, and an implementation must choose wether to store quantities in coherent units (i.e. all lengths are internally converted to and stored as _meter_), or allow incoherent units (i.e. lengths can be stored as _meter_, _kilometer_, _foot_, or some other commensurable unit). Storing coherent units is easier to implement, but has some important downsides.

One big problem is that the binary representation of a quantity's magnitude is not preserved as the assignment from one unit to another involves scaling and sometimes offsets (i.e. fahrenheit to celsius). Worse still, this may introduce unexpected errors due to rounding and limited numerical precision, especially when dealing with floating-point values.

In some use cases it can also be desirable to require that users represent quantities in particular units in order to avoid unnecessary conversions and to make the code easier to reason about. For example, a physics simulations library may require that all calculations be performed in the SI system and allow conversions from and to imperial units only for input and output.

Some implementations use a hybrid approach where the multiplicative factor is stored alongside the quantity's magnitude and applied in calculations. Others introduce separate types for every available unit and implement the conversions via operator overloading or helper functions.

Dimensionless Quantities
------------------------

One detail that is often overlooked is the support for dimensionless quantities. Some libraries represent these as multiplicative scalars using built-in types, such as integers or floats. Others use dimensionality vectors that have all their exponents set to zero, which allows for seamless integration with other units. Some have no support at all.

It is important to note, however, that dimensionless quantities are not simply scalar values. In fact, many have their own unit symbols assigned. For example, angles can be expressed as _radians_ or _degrees_, proportions as _percent_ or _promille_, and ratios as _decibel_ or _partspermillion_. While mixing these is permitted mathematically, it may be problematic semantically.

Related Resources
=================

[Top](https://gmpreussner.com/research/dimensional-analysis-in-programming-languages#top) Updated: May 30, 2018

  
  
from Hacker News https://ift.tt/2J0PHdJ
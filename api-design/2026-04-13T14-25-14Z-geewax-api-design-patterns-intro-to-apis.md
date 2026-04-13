# API Design Patterns | Intro to APIs

Web APIs: programming interfaces exposed over a network
- expose **functionality** without distributing a "code library"
- enable communication between systems and services (safe + stable)

Characteristics of Web API
- builders of API have most control
- users of API have little to no control over the underlying logic being exposed

Reasons for Web APIs
- abstract computational requirements (i.e. avoid running on local clients)
- expose functionality without exposing intellectual property (algorithms, code, etc.)
- enable automation (i.e. avoid GUIs & human interaction)
- treat **functionality** like building blocks (API composition)

Remote Procedure Call (RPC) Web API
- good for stateless functionality (i.e. `predictWeather(postalCode = 37042)`
- focused on "doing" something (i.e. sending email, encrypting data, etc.)

Resource Oriented Web API
- good for "stateful" functionality
- reduce complexity by relying on a standard set of actions ("methods") across a
  limited setd of things ("resources")

Stateful
- requires knowledge of prioerty requests or previously stored data

Stateless
- independent & repeatable
- no knowledge needed of persisted data or previous requests

Criteria for Building an API
1. some desired functionality exists that users want
2. users want to interact **programatically** with the functionality.

Imagine a system that translates text text from one language to another. This
functionality could be exposed as a mobile application, but this approach would mean
that others could not develop with the functionality in their own programs/apps.

Good API - Operational
- API must do what users actualy want
- consider non-operational requirements (latency, accuracy of output, etc)

Good API - Expressive
- the interface for using the API should be clear and simple
- do not hide/obfuscated functionality indirectly via not providing actions for
  the requested behavior (e.g. using a text-translation API as language detector, but
  never wanting to actually translate text. In this case just build `DetectLanguage()`
  function & expose)

Good API - Simple
- avoid reducing the number of total RPCs (gets messy to maintain and reason about)
- aim to expose functionality in straightforward manner ("simple as possible, no simpler")


"make common case awesomes & advanced case possible"
- when adding feature for adv user, keep that hidden from a typical user only interested
  in the common case.
- always protect the common case & make the API easy to use, but also don't neglect advanced
  users

Good API - Predictable
- use consistent naming for input parametes/fields
- use standard convention for action names (i.e. List, Get, Create, Delete, Update)

Rarely does a user learn the API by reading documentation fully. Predictable APIs
allow users to make assumptions about resources and actions. If `TranslateText(text: string)`
uses the `text` as field name, don't have `DetectLanguage(inputText: string)` be `inputText`. This
breaks assumptions.

APIs build with well-known, well-defined, clear, and simple patterns tend to overall
be easier to use, reason about, and lean.

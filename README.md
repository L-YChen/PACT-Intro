# PACT-Intro
The purpose of this documentation is to provide an overview of the contract testing tool "[PACT](https://docs.pact.io/)" and a technical example for hands-on learning. For those with experience in API testing, go to the [workshop page](https://docs.pact.io/implementation_guides) and get the project in preferred programming language for an immediate start. 
## Content:
- Integration testing, 2 API testing approaches and comparison
- PACT
- PACT workshop
- Links
## Integration testing, 2 API testing approaches and comparison
- Integration Testing:

Integration testing in this context is a test between an API provider and an API consumer that asserts that the provider returns expected responses for a set of pre-defined requests, also known as contracts, to the consumer.
In a distributed system, testing the successful integration between distributed services is essential for ensuring that the services won’t fail in production just because they’re not speaking the same language. Below are two API testing approaches and comparisons.
- 1st approach - End-to-End Tests (E2E Tests):

In end-to-end tests (E2E tests), servers or containers are set up as well as dependencies so that provider and consumer are available in a production-like runtime environment. To execute the integration tests, the consumer is usually triggered by providing certain input in the user interface. The consumer then calls the provider and the test asserts (again in the UI) if the results meet the expectations defined in the contract.
- 2nd approach - Mocking/Consumer-Driven Contract Tests (CDC Tests):

In a mock test, we no longer set up a runtime environment but run isolated tests between the consumer and a mock provider and between a mock consumer and the real provider. CDC testing is a kind of mocking as described above, with the speciality that the contract is driven by the consumer rather than the provider.
- Comparison:

Among the 2 API testing approaches, E2E testing is less isolated, less stable and more complex; feedback time is typically longer. Data and environment set up for E2E testing are more troublesome. CDC testing is more isolated, less complex with easier data set up; feedback time is shorter. Additionally, API contracts for CDC testing are not dictated by the provider, thus will fit user cases better.

## PACT

PACT is a contract testing tool. Contract testing is a kind of mock testing to ensure that the API microservices can communicate with each other without the hassle of E2E integration testing. Supported languages are Ruby, JVM, .NET, JavaScript, GO, Swift/Objective-C
### How PACT works

A pact is a contract between a consumer and a provider. Each pact (graph below) is a collection of interactions, and each interaction describes an expected request and a minimal expected response. CDC testing consists of 2 parts: consumer testing and provider verification.

![image](https://github.com/L-YChen/PACT-Intro/blob/master/A%20Pact.png)

For each iteration, Consumer Pact testing (graph below) checks whether the consumer code correctly generates the request and handles the expected response when the mock provider returns the expected response for this request. 

![image](https://github.com/L-YChen/PACT-Intro/blob/master/Consumer%20Testing.png)

Provider verification, on the other hand, is driven by the PACT framework. Each request from the mock consumer is sent to the real provider, and the actual response it generates is compared with the minimal expected response (graph below). 

![image](https://github.com/L-YChen/PACT-Intro/blob/master/Provider%20Verification.png)

Pairing the consumer PACT test and provider verification for each iteration, the contract between the consumer and provider is fully tested without having to spin up the services together (graph below).

![image](https://github.com/L-YChen/PACT-Intro/blob/master/A%20PACT%20Test%20Pair.png)
## Pact Workshop
The workshop includes a demo project with 3 components, a consumer project and two service providers, and provides descriptions of each step. The steps cover most functions PACT supports and following the steps one can expect to gain a deeper understanding of how PACT can be implemented and how it adds value to the framework. 

*PACT workshop is also available in Ruby, JVM, JS[2]*

## Links
- [PACT docs](https://docs.pact.io/)
- [PACT workshop](https://docs.pact.io/implementation_guides)
- [FAQ](https://docs.pact.io/faq)

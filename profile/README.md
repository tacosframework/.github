# **TACOS: Trusted Attestation and Compliance for Open Source**

## **Welcome to TACOS! 🌮**

TACOS is a framework for attesting to the secure software development practices of open source packages. TACOS stands for *Trusted Attestation and Compliance for Open Source*.  http://tacosframework.dev  🌮 🌮

## **TACOS is…**

A **framework** for assessing the development practices of open source projects against a set of secure development standards specified by the [NIST Secure Software Delivery Framework (SSDF) V1.1](https://csrc.nist.gov/Projects/ssdf). In this new era where software producers doing business with the U.S. government are being asked to attest that they are following NIST-defined secure software development practices (including the open source dependencies they use in their products), TACOS provides a framework that vendors can use to provide self-attestation for the open source components they rely on.

TACOS defines a machine-readable specification that software vendors can use as a part of their overall self-attestation paperwork to comply with [OMB memorandum M-22-18](https://blog.tidelift.com/key-dates-memorandum-m-22-18) requirements and deadlines. Organizations selling software to the U.S. government must attest that they comply with the NIST framework by as soon as June 2023 (for critical software) and September 2023 (for all software).

TACOS is grounded in the [NIST SSDF](https://csrc.nist.gov/Projects/ssdf), and draws from the [OpenSSF Scorecard](https://github.com/ossf/scorecard) and the [Center for Internet Security Software Supply Chain Security Guide](https://www.cisecurity.org/insights/white-papers/cis-software-supply-chain-security-guide). The TACOS framework is authored by Tidelift and is a unique outcome of our continued work with [partnered maintainers](https://tidelift.com/about/lifter), but all contributions are welcome.

The NIST SSDF v. 1.1 categories of secure software development practices are:

1.  **Prepare the organization:** Organizations should ensure that people, processes, and technology are prepared to perform secure software development at the organization level.
2.  **Protecting the software:** Organizations should protect all components of their software from tampering and unauthorized access.
3.  **Produce well-secured software:** Organizations should leverage people, processes and tools to produce well-secured software with minimal security vulnerabilities in its releases.
4.  **Respond to vulnerabilities:** Organizations should identify residual vulnerabilities in their software releases and have process and accountability to respond appropriately to those vulnerabilities and prevent similar ones from occurring in the future.

***Why do we need TACOS?***
Organizations seeking to improve software security outcomes will need to better understand how closely each open source component they rely on aligns with secure development standards. How can software vendors do this at scale, across the thousands of open source packages? With TACOS, of course.

TACOS gives organizations a proven and trusted framework for assessing the attestation and compliance practices of the open source packages they use. This, in turn, allows them to make better and more informed decisions regarding the open source they bring into their applications and to use this information to meet government attestation requirements.

We intend for TACOS to play well by design with [SLSA](https://slsa.dev/) (Supply chain Levels for Software Artifacts) and [GUAC](https://security.googleblog.com/2022/10/announcing-guac-great-pairing-with-slsa.html) (Graph for Understanding Artifact Composition) in this early design phase, and into the future. The SLSA framework provides a standardized way to attest to artifact provenance, and similarly TACOS provides a standardized way to attest to secure development practices in open source.

## **TACOS is a free framework—not free data**
At Tidelift, we partner with open source maintainers and pay them to implement and attest that they follow a clear set of secure development standards—including those outlined in the NIST SSDF. The outcome of this work for software producers is verified, first-party data, adhering to the TACOS attestation framework, that they can use to confidently attest to the security practices of the open source components they rely on.

**The work effort and the value delivered by open source maintainers must become visible and rewarded with both financial and non-financial rewards they deserve. This attestation data is extremely valuable, and if TACOS provides a way for more maintainers to be paid to work on it, that's a world we want to live in. We hope you do too!**  

## **What Does a TACOS attestation look like?**

A TACOS attestation is a simple data structure that contains the attestation metadata and statements attesting to the open source packages’ secure software development practices. (Read the full definition set in the [documentation repository](https://github.com/tacosframework/documentation) and see the complete field set in the [TACOS-spec repository](https://github.com/tacosframework/TACOS-spec)):

```
{
  "@context": "domain/namespace",
  "@id": "document URL",
  "signature": {"type": "sha256", "digest": "78ab8..."},
  "author": "Firstname Lastname",
  "role": "Attestor",
  "timestamp": "2022-03-23T05:35.37:00+04:00",
  "TACOSversion": "1",
  "application": "HelloWorld",
  "statements": [
    {
      "PackageName": "com.fasterxml.jackson.core:jackson-databind",
	    "PackagePlatform": "maven",
	    "PURL": "pkg:maven/com.fasterxml.jackson.core/jackson-databind",
      "UpstreamRepositoryURL": "https://github.com/FasterXML/jackson",
      "SPDXLicenseLatestRelease": "Apache-2.0", 
      "LatestRelease": "2.14.2",
      "ReleasesInUse": ["2.14.2, 2.14.0, 2.9.8"],
      "SBOM": [
      {
            "type": "cycloneDX",
            "version": "1.2",
            "format": "XML",
            "DigitalSignatureURL": "https://tidelift.com/packages/maven/com.fasterxml.jackson.core:jackson-databind-latest-cycloneDX.xml.sig",
            "URL": "https://tidelift.com/packages/maven/com.fasterxml.jackson.core:jackson-databind-latest-cycloneDX.xml"
	},
	{
            "type": "SPDX",
            "version": "2.3",
            "format": "SPDX",
            "DigitalSignatureURL": "https://tidelift.com/packages/maven/com.fasterxml.jackson.core:jackson-databind-latest-SPDX.spdx.sig",
            "URL": "https://tidelift.com/packages/maven/com.fasterxml.jackson.core:jackson-databind-latest-SPDX.spdx"
      }
      ],
     "PackageManager2FAEnabled": "True",
     "SourceRepo2FAEnabled": "True",
     "KnownReleasesURL":  "https://tidelift.com/packages/maven/com.fasterxml.jackson.core:jackson-databind/releases-map",
      ... and so on ...    
    }
  ]
}
```


You can see complete, more detailed, examples in the [examples repository](https://github.com/tacosframework/examples).

# Frequently Asked Questions

**Why do we need this framework?**
 -   Over the last few years it has become clear to us that reactive approaches like scanning for and addressing known vulnerabilities, while valuable, are not by themselves enough to get us the security outcomes the industry needs. The NIST SSDF explicitly states that additional measures beyond scanning for vulnerabilities must be implemented to improve cybersecurity outcomes.
 -   In addition to reactive efforts, organizations should be investing in proactive efforts that improve the health, security, and overall resilience of the open source software supply chain.
 -   TACOS gives organizations a way to measure and attest to the impact of these proactive efforts — development practices at the key moments when the open source software is being incepted, developed, and built—not just after it has shipped.
    
**Why aren’t you open sourcing the data?**
 -   Adding security practices like those required under the NIST SSDF is difficult and time consuming work for open source maintainers. People in your organization are being paid to ensure your own software development practices meet a high security standard. We should not expect maintainers to do this work for free. So Tidelift pays maintainers (with money provided by our customers) to complete the work of ensuring their packages follow secure software development practices like those recommended in the NIST SSDF. If this data is provided for free, maintainers don’t get paid, and there is no incentive for them to do the extra work.
    
**Is this specification useful without the data?**
 -   Yes. It provides a framework for the type of proactive secure development practices open source users should look for in the open source components they rely on.
 -   There are many credible, valuable projects and products in the software supply chain security space that have put forward powerful frameworks to govern and attest to provenance data, digital signatures, vulnerability exploit predictions, and vulnerability applicability. TACOS follows in those footsteps to meet this specific moment of accountability on how software is being built to attest to software practices throughout an upstream library’s lifecycle.
 -   TACOS defines first-party data from maintainers, and in particular continuous research into deprecation/maintenance status and income streams, as a strong flag in the ground on what secure software development looks like, and the resources required to accomplish those practices.
    
**What’s the relationship between TACOS and SBOMs?**
 -   An SBOM should be generated at build time and is then valid for the life of the application; TACOS references point in time information and thus evolves as development practices and dependency graphs change over time.
 -   That said, TACOS is designed to be SBOM format agnostic as part of a suite of M-22-18 attestation documentation, and includes a place for both CycloneDX and SPDX SBOMs for the latest release of each open source package as part of the v1 specification. This will ultimately allow for SBOM chaining to create a clear dependency graph for attesting to a software producers’ understanding and risk management. The intent is for TACOS attestation files to be continuously generated, signed and hosted alongside the continuous production of SBOMs, due to the transient nature of dependencies, and dependency graphs, used in applications.
 - A TACOS json file can be linked into either spec as a complementary
   artifact in the attestation process:
   -   [CycloneDX](https://cyclonedx.org/docs/1.4/json/#externalReferences)
   -   [SPDX](https://spdx.github.io/spdx-spec/v2.3/package-information/#721-external-reference-field)
-   Future versions of TACOS may integrate more natively with CycloneDX’s [component properties](https://cyclonedx.org/docs/1.4/json/#components_items_properties), their forthcoming bills of attestations feature, or a proposed native addition to the SPDX specification.
-   The Tidelift implementation of TACOS ingests an SBOM from any point in the SDLC and furnishes the attestation documentation required for upstream open source application libraries.
    
**What’s the difference between TACOS and OpenSSF Scorecard checks?**
-   The [OpenSSF Scorecard](https://github.com/ossf/scorecard) is another great resource for validating open source security practices. It was designed to help open source maintainers improve their security best practices and to help open source consumers judge whether their dependencies are safe.
-   TACOS was designed to meet the specific practices identified in the NIST SSDF v1.1 and on a timeline to be enforced by the U.S. Government to ensure that there are organizational, protective, production, and responsiveness practices in place to secure the software supply chain.
-   A notable difference between the two is that TACOS captures human-validated attestation data about the creation and delivery of the software. OpenSSF Scorecards assess open source projects for security risks through a series of automated checks.
    
**Should open source packages be held to this set of standards?**
-   TACOS is being built to declare what set of secure development standards open source projects should uphold in order to secure the software supply chain, and give us the greatest chance of our desired outcome: reducing problems upstream.
-   Tidelift, the original creator behind TACOS, does not believe that any open source package maintainer or contributor owes any work to meet, or attest to, these standards in the absence of equitable value exchange for the time it takes to produce this work.
-   Please do not push this framework or attestation requests onto any open source maintainer as additional unpaid labor.

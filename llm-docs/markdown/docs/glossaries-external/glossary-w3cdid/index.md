# External W3C DID Glossary

\[ [A](#amplificationattack) | [B](#undefined) | [C](#cryptographicsuite) | [D](#decentralizedidentifier\(DID\)) | [E](#undefined) | [F](#undefined) | [G](#undefined) | [H](#undefined) | [I](#undefined) | [J](#undefined) | [K](#undefined) | [L](#undefined) | [M](#undefined) | [N](#undefined) | [O](#undefined) | [P](#publickeydescription) | [Q](#undefined) | [R](#resource) | [S](#services) | [T](#undefined) | [U](#UniformResourceIdentifier\(URI\)) | [V](#verifiablecredential) | [W](#undefined) | [X](#undefined) | [Y](#undefined) | [Z](#undefined) \]

amplification attack

A class of attack where the attacker attempts to exhaust a target system'sCPU, storage, network, or other resources by providing small, valid inputs intothe system that result in damaging effects that can be exponentially more costlyto process than the inputs themselves.

authenticate

Authentication is a process by which an entity can prove it has a specificattribute or controls a specific secret using one or more verificationmethods. With DIDs, a common example would be proving control of thecryptographic private key associated with a public key published in a DIDdocument.

cryptographic suite

A specification defining the usage of specific cryptographic primitives inorder to achieve a particular security goal. These documents are often usedto specify verification methods, digital signature types,their identifiers, and other related properties.

decentralized identifier (DID)

A globally unique persistent identifier that does not require a centralizedregistration authority and is often generated and/or registeredcryptographically. The generic format of a DID is defined in 3.1 DID Syntax. A specific DID scheme is defined in a DIDmethod specification. Manybut not allDID methods make use ofdistributed ledger technology (DLT) or some other form of decentralizednetwork.

decentralized identity management

Identitymanagement that is based on the use of decentralized identifiers.Decentralized identity management extends authority for identifier generation,registration, and assignment beyond traditional roots of trust such asX.500 directory services,the Domain Name System,and most national ID systems.

DID controller

An entity that has the capability to make changes to a DID document. ADID might have more than one DID controller. The DID controller(s)can be denoted by the optional controller property at the top level of theDID document. Note that a DID controller might be the DIDsubject.

DID delegate

An entity to whom a DID controller has granted permission to use averification method associated with a DID via a DIDdocument. For example, a parent who controls a child's DID documentmight permit the child to use their personal device in order toauthenticate. In this case, the child is the DID delegate. Thechild's personal device would contain the private cryptographic materialenabling the child to authenticate using the DID. However, the childmight not be permitted to add other personal devices without the parent'spermission.

DID document

A set of data describing the DID subject, including mechanisms, such ascryptographic public keys, that the DID subject or a DID delegatecan use to authenticate itself and prove its association with theDID. A DID document might have one or more differentrepresentations as defined in 6. Representations or in theW3C DID Specification Registries \[DID-SPEC-REGISTRIES\].

DID fragment

The portion of a DID URL that follows the first hash sign character(#). DID fragment syntax is identical to URI fragment syntax.

DID method

A definition of how a specific DID method scheme is implemented. A DID method isdefined by a DID method specification, which specifies the precise operations bywhich DIDs and DID documents are created, resolved, updated,and deactivated. See 8. Methods.

DID path

The portion of a DID URL that begins with and includes the first forwardslash (/) character and ends with either a question mark(?) character, a fragment hash sign (#) character,or the end of the DID URL. DID path syntax is identical to URI path syntax.See Path.

DID query

The portion of a DID URL that follows and includes the first questionmark character (?). DID query syntax is identical to URI querysyntax. See Query.

DID resolution

The process that takes as its input a DID and a set of resolutionoptions and returns a DID document in a conforming representationplus additional metadata. This process relies on the "Read" operation of theapplicable DID method. The inputs and outputs of this process aredefined in 7.1 DID Resolution.

DID resolver

A DID resolver is a software and/or hardware component that performs theDID resolution function by taking a DID as input and producing aconforming DID document as output.

DID scheme

The formal syntax of a decentralized identifier. The generic DID schemebegins with the prefix did: as defined in 3.1 DID Syntax. Each DID method specification defines a specificDID method scheme that works with that specific DID method. In a specific DIDmethod scheme, the DID method name follows the first colon and terminates withthe second colon, e.g., did:example:

DID subject

The entity identified by a DID and described by a DID document.Anything can be a DID subject: person, group, organization, physical thing,digital thing, logical thing, etc.

DID URL

A DID plus any additional syntactic component that conforms to thedefinition in 3.2 DID URL Syntax. This includes an optional DIDpath (with its leading / character), optional DID query(with its leading ? character), and optional DID fragment(with its leading # character).

DID URL dereferencing

The process that takes as its input a DID URL and a set of inputmetadata, and returns a resource. This resource might be a DIDdocument plus additional metadata, a secondary resourcecontained within the DID document, or a resource entirelyexternal to the DID document. The process uses DID resolution tofetch a DID document indicated by the DID contained within theDID URL. The dereferencing process can then perform additional processingon the DID document to return the dereferenced resource indicated by theDID URL. The inputs and outputs of this process are defined in7.2 DID URL Dereferencing.

DID URL dereferencer

A software and/or hardware system that performs the DID URL dereferencingfunction for a given DID URL or DID document.

distributed ledger (DLT)

A non-centralized system for recording events. These systems establishsufficient confidence for participants to rely upon the data recorded by othersto make operational decisions. They typically use distributed databases wheredifferent nodes use a consensus protocol to confirm the ordering ofcryptographically signed transactions. The linking of digitally signedtransactions over time often makes the history of the ledger effectivelyimmutable.

public key description

A data object contained inside a DID document that contains all themetadata necessary to use a public key or a verification key.

resource

As defined by \[RFC3986\]: "...the term 'resource' is used in a general sensefor whatever might be identified by a URI." Similarly, any resource might serveas a DID subject identified by a DID.

representation

As defined for HTTP by \[RFC7231\]: "information that is intended to reflect apast, current, or desired state of a given resource, in a format that can bereadily communicated via the protocol, and that consists of a set ofrepresentation metadata and a potentially unbounded stream of representationdata." A DID document is a representation of information describing aDID subject. See 6. Representations.

representation-specific entries

Entries in a DID document whose meaning is particular to a specificrepresentation. Defined in 4. Data Model and6. Representations. For example, @context inthe JSON-LD representation is arepresentation-specific entry.

services

Means of communicating or interacting with the DID subject orassociated entities via one or more service endpoints.Examples include discovery services, agent services, social networkingservices, file storage services, and verifiable credential repository services.

service endpoint

A network address, such as an HTTP URL, at which services operate onbehalf of a DID subject.

Uniform Resource Identifier (URI)

The standard identifier format for all resources on the World Wide Web asdefined by \[RFC3986\]. A DID is a type of URI scheme.

verifiable credential

A standard data model and representation format for cryptographically-verifiabledigital credentials as defined by the W3C Verifiable Credentials specification\[VC-DATA-MODEL\].

verifiable data registry

A system that facilitates the creation, verification, updating, and/ordeactivation of decentralized identifiers and DID documents. Averifiable data registry might also be used for othercryptographically-verifiable data structures such as verifiablecredentials. For more information, see the W3C Verifiable Credentialsspecification \[VC-DATA-MODEL\].

verifiable timestamp

A verifiable timestamp enables a third-party to verify that a data objectexisted at a specific moment in time and that it has not been modified orcorrupted since that moment in time.If the data integrity could reasonably havebeen modified or corrupted since that moment in time, the timestamp is notverifiable.

verification method

A set of parameters that can be used together with a process to independentlyverify a proof. For example, a cryptographic public key can be used as averification method with respect to a digital signature; in such usage, itverifies that the signer possessed the associated cryptographic private key. "Verification" and "proof" in this definition are intended to apply broadly. Forexample, a cryptographic public key might be used during Diffie-Hellman keyexchange to negotiate a shared symmetric key for encryption. This guarantees theintegrity of the key agreement process. It is thus another type of verificationmethod, even though descriptions of the process might not use the words"verification" or "proof."

verification relationship

An expression of the relationship between the DID subject and averification method. An example of a verification relationship is5.3.1 Authentication.

Universally Unique Identifier (UUID)

A type of globally unique identifier defined by \[RFC4122\]. UUIDs are similarto DIDs in that they do not require a centralized registration authority. UUIDsdiffer from DIDs in that they are not resolvable orcryptographically-verifiable.
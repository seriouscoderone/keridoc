# External ToIP did:webs Glossary

\[ [A](#AIDcontrolledidentifiers) | [B](#BADARUN) | [C](#compacteventstreamingrepresentation\(CESR\)) | [D](#decentralizedidentifier\(DID\)) | [E](#undefined) | [F](#undefined) | [G](#undefined) | [H](#host) | [I](#inceptionevent) | [J](#undefined) | [K](#keyevent) | [L](#undefined) | [M](#methodspecificidentifier) | [N](#undefined) | [O](#outofbandintroduction\(OOBI\)) | [P](#prerotation) | [Q](#undefined) | [R](#rotationevent) | [S](#selfaddressingidentifier\(SAID\)) | [T](#transactioneventlog\(TEL\)) | [U](#undefined) | [V](#verifier) | [W](#watcher) | [X](#undefined) | [Y](#undefined) | [Z](#undefined) \]

AID controlled identifiers

Any identifier, including did:webs DIDs, that have the same AID are by definition referencing the same identity. As defined in the KERI specification

authentic chained data container (ACDC)

a variant of the Verifiable Credential (VC) specification that inherits the security model derived from KERI, as defined by the ACDC specification. See WebOfTrust glossary for more detail.

autonomic identifier (AID)

A self-certifying identifier (SCID) that is cryptographically bound cryptographically bound to a key event log (KEL), as defined by the KERI specification. An AID is either non-transferable or transferable. A non-transferable AID does not support key rotation while a transferable AID supports key rotation using a key pre-rotation mechanism that enables the AID to persist in spite of the evolution of its key state. See WebOfTrust glossary for more detail.

BADA-RUN

Best available data acceptance - Read/Update/Nullify provides a medium level of security because events are ordered in a consistent way, using a combination of date-time and a key state. The latest event is the one with the latest date-time for the latest key state. See The KERI spec for more detail.

compact event streaming representation (CESR)

An encoding format that enables round-trip text-binary conversion of concatenated cryptographic primitives and general data types, as defined by the CESR specification and CESR Proof Signature specification. See WebOfTrust glossary for more detail.

controller

A controlling entity that can cryptographically prove the control authority (signing and rotation) over an AID as well as make changes on the associated KEL. A controller may consist of multiple controlling entities in a multi-signature scheme. See WebOfTrust glossary for more detail.

decentralized identifier (DID)

A globally unique persistent identifier, as defined by DID Core.

designated aliases

An array of AID controlled identifiers that have been designated by the AID controller to be used as aliases for equivalentId and alsoKnownAs DID document metadata and to foster verification of redirection to different did:webs identifiers. See WebOfTrust glossary for more detail.

DID document

A set of data describing the subject of a DID, as defined by DID Core. See also section DID Documents.

DID resolution metadata

DID resolution metadata is metadata about the DID Resolution process that was performed in order to obtain the DID document for a given DID. See also DID Resolution Metadata in the DID Core specification.

DID document metadata

DID document metadata is metadata about the DID and the DID document that is the result of the DID Resolution process. See also DID Document Metadata in the DID Core specification.

direct mode

an operational mode of the KERI protocol where a controller and a verifier of an AID exchange the KEL of the AID directly, as defined by the KERI whitepaper. See WebOfTrust glossary for more detail.

host

The part of a URL that can be either a domain name or an IP address. This component specifies the server that the client needs to communicate with in order to access the desired resource on the web.

inception event

A key event that provides the incepting information needed to derive an AID and establish its initial key state, as defined by the KERI specification. See WebOfTrust glossary for more detail.

indirect mode

An operational mode of the KERI protocol where the KEL of an AID is discovered by a verifier via witnesses, as defined by the KERI whitepaper. See WebOfTrust glossary for more detail.

interaction event

A key event that anchors external data to an AID, as defined by the KERI specification. An interaction event does not change the key state of the AID. See WebOfTrust glossary for more detail.

key event

A serialized data structure of an entry in the key event log(KEL) for an AID, as defined by the KERI specification. There are three types of key events, namely inception event, rotation event, and interaction event. See WebOfTrust glossary for more detail.

key event log (KEL)

A verifiable append-only log of key events for an AID that is both backward and forward-chained, as defined by the KERI specification. See WebOfTrust glossary for more detail.

KEL backed data

KEL backed data in did:webs provides the highest level of data security assurance and such data can be found either in the KEL or anchored to an event in the KEL. This means that the signatures on the events in the KEL are strongly bound to the key state at the time the events are entered in the KEL, that is the data. This provides strong guarantees of non-duplicity to any verifiers receiving a presentation as the KELs are protected and can be watched by agents (watcher) of the verifiers. The information is end-verifiable and any evidence of duplicity in the events is evidence that the data or presentation should not be trusted. See WebOfTrust glossary for more detail.

key event receipt

A message whose body references a key event of an AID and includes one or more signatures on that key event, as defined by the KERI specification. See WebOfTrust glossary for more detail.

key event receipt log (KERL)

A verifiable append-only log that includes all the consistent key event receipt messages, as defined by the KERI specification. See WebOfTrust glossary for more detail.

key event receipt infrastructure (KERI)

A protocol that provides an identity system-based secure overlay for the internet and uses AIDs as the primary roots of trust, as defined by the KERI specification. See WebOfTrust glossary for more detail.

KERI event stream

A stream of verifiable KERI data, consisting of the key event log (KEL) and other data such as a transaction event log (TEL). This data is a CESR event stream, with media type application/cesr, and may be serialized in a file using CESR encoding. We refer to these CESR stream resources as KERI event streams to simplify the vocabulary. See WebOfTrust glossary for more detail.

key state

The set of currently authoritative key pairs (current keys) for an AID and any other information necessary to secure or establish control authority over the AID. See WebOfTrust glossary for more detail.

KERI Request Authentication Mechanism

A non-interactive replay attack protection algorithm that uses a sliding window of date-time stamps and key state (similar to the tuple in BADA-RUN) but the date-time is the repliers not the queriers. KRAM is meant to protect a host. See the WebOfTrust glossary for more detail.

method-specific identifier

The method-specific-id part of DID Syntax, as defined in DID Core. See section Method-Specific Identifier.

multi-signature

A mechanism that enables multiple parties to sign a message, as defined by the KERI specification. See Controller Application in the KERI spec for more detail.

out-of-band introduction (OOBI)

A protocol for discovering verifiable information on an AID or a SAID, as defined by the KERI specification. The OOBI by itself is insecure, and the information discovered by the OOBI must be verified. See WebOfTrust glossary for more detail.

pre-rotation

A key rotation mechanism whereby a set of rotation keys are pre-commited using cryptographic digests, as defined by the KERI specification. See WebOfTrust glossary for more detail.

rotation event

A key event that provides the information needed to change the key state for an AID using pre-rotation, as defined by the KERI specification. See WebOfTrust glossary for more detail.

self-addressing identifier (SAID)

An identifier that is uniquely and cryptographically bound to a serialization of data (content-addressable) while also being included as a component in that serialization (self-referential), as defined by the CESR specification. See WebOfTrust glossary for more detail.

transaction event log (TEL)

A verifiable append-only log of transaction data that are cryptographically anchored to a KEL. The transaction events of a TEL may be used to establish the issuance or revocation state of ACDCs. See WebOfTrust glossary for more detail.

verifier

An entity or component that cryptographically verifies the signature(s) on an event message. See WebOfTrust glossary for more detail.

watcher

An entity that keeps a copy of a KERL of an AID to detect duplicity of key events, as defined by the KERI whitepaper. See WebOfTrust glossary for more detail.

witness

An entity that is designated by the controller of an AID to verify, sign, and keep the key events associated with the AID, as defined by the KERI whitepaper. See WebOfTrust glossary for more detail.

w
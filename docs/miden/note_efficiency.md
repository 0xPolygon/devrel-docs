# Miden's Note Efficiency

Miden's approach to note efficiency is a key differentiator in the landscape of
privacy-focused blockchains. By leveraging innovative techniques for note
discovery and management, Miden ensures both privacy and efficiency in handling
transactions. This document explores the mechanisms behind Miden's note
efficiency and how they contribute to a seamless user experience.

As a reminder, Miden supports three types of notes: public, private, and
encrypted. You can learn more about them in the [Miden Notes](./note_types.md)
document.

## Efficient Note Discovery

One of the standout features of Miden is its efficient note discovery process.
Unlike other systems that require decrypting all records to discover private
states, Miden uses a tagging mechanism to streamline this process.

![Robot confused at a box of unknown notes](../images/note_eff_02.jpeg)

### Tagging Mechanism

In Miden, each note is assigned a tag, which can be used to request notes. This
allows users to request a subset of all notes, significantly reducing the amount
of data that needs to be processed.

![Robot looking at smaller boxes of fewer notes](../images/note_eff_01.png)

The tagging mechanism introduces some "fuzziness," meaning users may receive
some notes that are not theirs, but this can be controlled to balance privacy
and efficiency.

### User-Defined Tags

Users have the flexibility to choose their tags or use default strategies
provided by Miden. For example, a common strategy is to use the first 16 bits of
the user's account ID as a tag. This approach ensures that as the number of
accounts grows, the likelihood of tag collisions increases, enhancing privacy
through obfuscation.

![Privacy through obfuscation](../images/note_eff_03.jpeg)

### Requesting Notes

Users can request notes by their tags, allowing them to efficiently discover
which notes belong to them without downloading all notes. This process is not
only efficient but also privacy-preserving, as users can control the rate of
false positives and even request all notes if they wish to hide their interests
from the node.

## Conclusion

Miden's innovative approach to note management and discovery sets it apart in
the realm of privacy-focused blockchains. By leveraging public, private, and
encrypted notes, along with an efficient tagging mechanism, Miden ensures both
privacy and efficiency for its users. This design allows for a seamless and
secure user experience, making Miden a compelling choice for privacy-conscious
applications.

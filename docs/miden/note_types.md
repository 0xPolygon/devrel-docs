# Note types

To learn about the architecture of Notes in Miden, you can read the
[technical docs](https://docs.polygon.technology/miden/miden-base/architecture/notes/).

This document's focus is on the different types of Notes and what they're used
for.

Three types of Notes exist in Miden:

- public
- private
- encrypted (not yet supported)

## Commonalities

In all three cases, a note's nullifier needs to be computed so the note can be
"used up." Miden stores the nullifier in the notes nullifier database.

A note's execution - whether private or public - happens when something called
the Transaction Kernel executes. The kernel executes on the Miden VM - and
so, for every execution, the VM generates a STARK proof that the kernel was executed
correctly. This part is applied differently for private and public notes.

To compute a note's nullifier, Miden needs to know the following:

- commitment to the note's assets.
- commitment to the note's script.
- commitment to the note's inputs.
- the note's serial number.

Miden doesn't have to know all the private details (for example, the actual
assets or the actual note script), but sometimes the clients do have them
(public notes).

## Public notes

With Public notes, all note details are recorded on-chain. For example, if
Alistair is sending a note to Bob, Alistair will send all note details _to_ the
network (i.e., the Miden node), and then Bob will get all note details _from_
the network.

So, there is no need for Alistair and Bob to communicate directly. With public
notes, the network (e.g., node operators) executes the Transaction Kernel. To do
so, they must know all the details of a transaction, and so all transaction
information must be public.

In this way, public notes are similar to how Bitcoin transactions work now, with
the added advantage of being able to run scripts.

_Example:_ An animal shelter charity organization has four different facets of
their activity: buying food, buying blankets, buying vet care, and subsidizing
walkers. You trigger a function in each one by calling its respective smart
contract function while donating. Alistair wants to donate to the "buy a puppy
blanket", so his script calls this function while depositing the assets.

## Private notes

With Private notes, only the note hash is recorded on-chain. Alistair would send
the note hash to the network and would also send all note details to Bob
directly.

The Kernel is also executed locally by the user, and then the results are sent
to the network. Here, assuming the proving scheme is ZK, no information beyond
what the user sends to the network is leaked.

Because of this, when dealing with private notes, Alistair and Bob need to have
a side-channel of communication open. They need to exchange the note data because
when Alistair sends the note to Bob, Bob needs to run it locally somehow - and
that's only possible if they have the note data.

_Example:_ A note contains a script for a voting system where users can cast
their votes on-chain. The script ensures that each user can vote only once and
that all votes are publicly verifiable as being cast, but not public. The Miden
network executes the script, tallying the votes and ensuring transparency and
integrity in the voting process while preventing bribery.

## Encrypted notes

Encrypted notes are not yet supported.

Encrypted notes are conceptually similar to public notes, but instead of sending
notes in plain text to the network, Alistair would encrypt it first. This way,
the contents of the note do not need to be public, but also, Alistair and Bob do
not need to have a side channel to communicate.

This model assumes there was a key exchange of some sort beforehand, possibly
such that the keys are in a common Miden registry only accessible to the two
parties.

Alternatively, it is possible that Miden will, in this case, be used purely as
a "data availability" layer and that the actual execution will happen off-chain
once Bob takes the encrypted note and decrypts it, which again assumes a
pre-existing side-channel for key exchange between Alistair and Bob.

_Example:_ Alistair wants to share encrypted medical data with Bob, who is a
researcher. Alistair encrypts the data and includes a script that performs
statistical analysis on the data. He sends the encrypted note to the Miden
network. Bob, who has the decryption key, retrieves the encrypted note, decrypts
it, and runs the script to perform the analysis. This ensures that the data
remains confidential while allowing Bob to perform necessary computations.

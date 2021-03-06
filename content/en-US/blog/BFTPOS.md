~~~
title: "BFT: The Most Secure Proof-of-Stake"
slug: bft-the-most-secure-proof-of-stake
date: 2016-11-15
author: Jae Kwon
excerpt: Many people have rallied against the use of PoS, claiming it is impossible to secure. But that is simply not true. Using BFT, you absolutely can secure PoS.  It’s just that we haven’t seen any BFT-PoS public blockchains yet.
~~~

Bitcoin brought the world’s attention to the blockchain. But alas, the Bitcoin
version of blockchain isn’t sufficient for the world’s blockchain needs. That
is because Bitcoin’s proof of work (PoW) consensus [requires an enormous amounts
of energy](http://motherboard.vice.com/read/bitcoin-could-consume-as-much-electricity-as-denmark-by-2020). In addition, transactions are painstakingly slow, taking an hour or
longer to commit. And because PoW miners have little incentive to be loyal to
one chain or other, upgrades are difficult to coordinate.
 
We need an approach to manage blockchains securely that does not impose a huge
energy cost on our planet. That approach is Byzantine fault-tolerance
(BFT)-based [proof-of-stake](https://bitcointalk.org/index.php?topic=27787.0) (PoS).  We call it BFT-PoS.
 
Before I delve into the merits of BFT-PoS, let me first address the concept of
Byzantine faults without going into confusing detail about [Lamport’s General
and his armies](http://pages.cs.wisc.edu/~sschang/OS-Qual/reliability/byzantine.htm). 

In a distributed system, where data is replicated across hundreds or thousands
of nodes, there needs to be some type of fault-tolerance or consensus
algorithm, for the simple fact that computers break down or go offline from
time to time. So if a portion of those nodes fail, the system as a whole still
needs to reach a consensus.
 
Standard fault-tolerant consensus algorithms like
[Raft](https://raft.github.io/raft.pdf) and
[Paxos](https://en.wikipedia.org/wiki/Paxos_(computer_science)) assume that
when a node fails, it simply stops working and doesn’t send back a reply.
Google, Facebook, and some existing database products already use this family
of consensus algorithms within their firewalls to ensure that services remain
available despite faulty computers.

But these algorithms aren’t suitable for public blockchains, because there is
no firewall in a public blockchain.  Anyone with mining power (in PoW) or
staking tokens (in PoS) can participate, or even try to sabotage the network.
To reach consensus on a public blockchain, we need Byzantine fault-tolerance.
In a Byzantine fault, the faulty node can behave in a completely arbitrary
manner. Nodes can even collude to try and maximize the damage they cause.
 
So essentially, the purpose of a BFT consensus algorithm is to establish trust
between otherwise unrelated parties over an untrusted network like the
Internet.
 
BFT is nothing new. The concept was first introduced in an academic paper by
[Lamport, Shostak, and Pease in
1982](http://research.microsoft.com/en-us/um/people/lamport/pubs/byz.pdf). But
Lamport et al only demonstrated the theoretical feasibility of the algorithm in
a synchronous environment, where all the messages always arrive on time.  
 
But in the real world, you can’t really trust the Internet to deliver anything
on time. So in 1988, [Dwork, Lynch, and Stockmeyer](http://groups.csail.mit.edu/tds/papers/Lynch/jacm88.pdf) (DLS) proposed an algorithm
that works in mostly asynchronous environments.  Later in 1999, [Miguel Castro
and Barbara Liskov](http://pmg.csail.mit.edu/papers/osdi99.pdf) proposed a practical solution for continuous BFT consensus
that was, and still is today, the state-of-the-art in BFT algorithms.
 
But for a long time, the mainstream press ignored these seminal works. Nobody
understood the importance of BFT outside academia and major institutions like
IBM and DARPA, until 2009 when Bitcoin came along. Bitcoin was the first open
decentralized application to provide BFT consensus on a global currency ledger,
but using a completely novel solution to the Byzantine general’s problem: PoW.  
 
In PoW, miners compete, based on who has the most processing power, to validate
transactions. And for their efforts they are rewarded with transaction fees and
newly minted bitcoins. This is how Bitcoin creates new currency.  Bitcoin
miners around the globe compete in a lottery-like system for these newly issued
bitcoins, and the efficient market makes it so that the cost of the energy used
by the global mining network is on the order of the block reward (plus
transaction fees).  Today, that turns out to be around $1M worth of electricity
per day.  In addition, Bitcoin mining is being commoditized by [large data
centers in places of the world where electricity is more affordable](https://bitcointalk.org/index.php?topic=1072474.0), making it
difficult for laymen to participate.
 
PoS, on the other hand, does away with the energy dependence of PoW entirely.
In PoS, miners are replaced with “validators” who have a stake in the system.
Validators don’t have to invest in expensive processing systems but they do
have to purchase “staking tokens.” Any normal laptop will suffice to solve the
algorithm.  
 
Peercoin, [BitShares](https://bitshares.org/),
[Nxt](https://en.wikipedia.org/wiki/Nxt), and others already use some form of
PoS, and Ethereum is planning a move to PoS in the near future. Yet, while PoS
makes practical sense, many people have [rallied against the use of
PoS](https://download.wpsoftware.net/bitcoin/pos.pdf), claiming it is
impossible to secure. But that is simply not true. Using BFT, you absolutely
can secure PoS.  It’s just that we haven’t seen any BFT-PoS public blockchains
yet.

While the theory may be difficult to explain or understand, the ultimate
results provided by proper BFT algorithms are simple to grasp.  Unlike PoW
blockchains, BFT-PoS blockchains do not fork (i.e. get double-spend attacked)
at all unless ⅓ or more validators coordinate such an attack.  And, when 1/3 or
more validators do cause a double-spend attack, we can computationally
determine which validators were responsible for the attack, destroy their
staking tokens and eject them from the network.  It’s as if the staking tokens
are virtualized PoW miners that blow up when used to attack the system.  No
other blockchain consensus algorithm, including PoW, can provide the level of
collateralization that is possible with BFT-PoS.

BFT-PoS performs extremely well. Today, in global public blockchain with a few
hundred validators, you can get transaction finality on the  order of 3
seconds, easily -- no need to wait for additional block confirmations! The
theory has proven to us that these are optimal fault-tolerance thresholds for
“instant-finality” blockchains.  While more validators does slow down
consensus, if [Nielsen’s
law](https://www.nngroup.com/articles/law-of-bandwidth/) continues to hold,
we’ll even be able to support an exponentially increasing number of validators
every year with the same performance.

In addition, BFT-PoS will also increase the security of mobile wallets. Few of
the mobile wallets in existence today take full advantage of the security
offered by Bitcoin, for the simple fact that nobody is willing to wait an hour
for a transaction to clear. Instead, most wallets just assume that [the person
sending the money isn’t trying to double spend
it](https://www.coingecko.com/buzz/peter-todd-explains-the-problems-with-unconfirmed-bitcoin-transactions).
And, though we don’t have time to dive into it here, efficient mobile wallet
protocols, or “light client SPV” protocols are the key to future blockchain
interoperability.

While PoW worked well for Bitcoin, it’s costly, slow, and environmentally
unfriendly. The best alternative out there right now is BFT-PoS. It’s an
enduring, energy efficient solution that works well in asynchronous
environments. And best of all, because BFT was developed by the best and the
brightest in the computer science industry, it’s provably secure. You can’t do
any better than that.

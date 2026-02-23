# ZLB: A Blockchain to Tolerate Colluding Majorities

> **Paper**: *ZLB: A Blockchain to Tolerate Colluding Majorities*
> **Authors**: Alejandro Ranchal-Pedrosa,Vincent Gramoli
> **Conference**: 2024 54th Annual IEEE/IFIP International Conference on Dependable Systems and Networks (DSN)
> **Links**: [IEEE](https://ieeexplore.ieee.org/abstract/document/10646997) | [arXiv](https://arxiv.org/abs/2305.02498) | [PDF](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10646997)

## Introduction (Aka What is this paper about)

Blockchain systems promise a decentralized way to record transactions without relying on a central authority. They aim to provide trust by having multiple independent participants agree on one version of history. But how strong is that trust? What happens when the assumptions that underpin these systems are pushed to extremes?

This paper, “ZLB: A Blockchain to Tolerate Colluding Majorities”, proposes a radical idea: a blockchain that can continue to operate safely even when a majority of its participants collude maliciously to disrupt it. Until now, most blockchain designs assumed that once a large enough fraction of participants misbehave, the system’s guarantees break down. This paper challenges that assumption and introduces a design that can detect, respond to, and recover from such powerful attacks.

Before we explore how one might do that, it helps to understand the problem this paper is trying to solve.

## Problem : Why Majority Attacks Are Dangerous
You may have heard about a “51 % attack” in the context of blockchain systems. But what does that really mean, and why is it so serious?

In many blockchains, especially those based on Proof-of-Work (PoW), the network’s security relies on no single participant or group controlling more than half of the system’s power (for example, hash power in PoW or stake in Proof-of-Stake). If an attacker or group of attackers gains majority control, they can manipulate which blocks are accepted and which are not.

But how does that translate into real harm?

When an attacker controls the majority, they can:
- Reverse previously confirmed transactions
- Create conflicting versions of the ledger
- Spend the same funds more than once (double-spend)
- Censor or exclude transactions requested by honest users

All of these outcomes undermine the fundamental guarantees of blockchain systems — **consistency**, **integrity**, and **fair execution** of transactions.

In simple terms , a majority attack doesn’t just break a protocol. It undermines the very trust that users place in decentralized systems.

## How Do Traditional Blockchains Handle Majority Risk?

Given how dangerous majority control can be, it is natural to ask:
> *How do existing blockchains protect themselves?*

Different systems rely on different assumptions.

In classical Byzantine Fault Tolerant (BFT) systems, safety is guaranteed only if fewer than one-third of the participants are malicious. Once that threshold is crossed, honest nodes may disagree, and consensus can no longer be guaranteed. The protocol does not “degrade gracefully” — it simply loses its guarantees.

In Proof-of-Work systems like Bitcoin, the assumption is slightly different. Instead of a strict one-third bound, security relies on economic majority. The idea is that no attacker will realistically control more than 50% of the total mining power because the cost would be enormous. As long as honest miners collectively control the majority of computational power, the system remains secure.

But notice what both approaches have in common:

They both rely on **majority honesty**.

If that assumption fails, so do the guarantees.

## But Isn’t 51% Unrealistic for Large Networks Like Bitcoin?
This is a fair question.

Acquiring 51% of Bitcoin’s hash power is extraordinarily expensive. It would require massive infrastructure, capital, and coordination. In that sense, Bitcoin is relatively secure due to its scale.

But does that mean majority attacks are not a real concern?

Not necessarily.

First, not all blockchains operate at Bitcoin’s scale. Smaller networks are far more vulnerable to concentration of power.

Second, mining power is often organized into pools. If a small number of large pools coordinate — or are compromised — the effective control structure can become more centralized than it appears.

Most importantly, from a systems perspective, security should ideally not depend purely on economic difficulty. The deeper question is not whether majority attacks are expensive today, but whether a blockchain protocol can remain robust even if majority control occurs.



## Real-World Examples of Majority Failures
One might think majority attacks are purely theoretical. Unfortunately, they are not.

Several smaller blockchain networks have suffered majority attacks in practice. For example:


- In 2014, the **Bitcoin blockchain** faced a potential 51% attack when a mining pool controlled over 50% of the network's hash rate. Although it was averted, it highlighted the vulnerability of decentralized systems to collusion.
- **Bitcoin Gold (BTG)** : In January 2020, Over $72,000 worth of BTG was double-spent during this attack, highlighting vulnerabilities in smaller PoW networks.
- **Ethereum Classic (ETC)** : In October 2025, A 51% attack was executed, costing over $144,000 for a 24-hour attack, demonstrating the risks for smaller networks. 

These cases highlight an important reality: blockchain security is conditional. It depends on the distribution of power within the network. When that distribution becomes skewed, the system becomes vulnerable.

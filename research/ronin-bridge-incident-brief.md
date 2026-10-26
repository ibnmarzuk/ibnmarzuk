# Case Brief: The Ronin Bridge Exploit (March 2022)

**Audience:** Non-technical readers  
**Focus:** Timeline, root cause, impact, user choices and lessons

## Executive summary

On 23 March 2022, attackers stole cryptocurrency from the Ronin Bridge, a service used to move assets between Ethereum and Ronin, a blockchain associated with the game Axie Infinity. The theft was discovered on 29 March after a user reported being unable to withdraw 5,000 ETH. Ronin reported that 173,600 ETH and 25.5 million USDC had been taken. Public estimates put the value at about $600 million to $625 million, depending on the prices and calculation date. The incident showed that a bridge can fail even when it requires multiple approvals if attackers gain control of enough of the people or systems authorized to approve withdrawals.

## How the bridge worked

A **blockchain** is a shared record of transactions maintained by a network of computers. A **bridge** helps move assets between separate blockchains. A **validator** is an operator whose approval helps authorize network activity. A **private key** is secret digital information used to prove authority and approve actions.

Ronin supported Axie Infinity. Its bridge had nine validator nodes, and five approvals were enough to authorize a withdrawal. That arrangement was meant to distribute authority, but control of five validators was sufficient to bypass the safeguard.

## Timeline

**November 2021:** According to Ronin’s incident explanation, Sky Mavis, the company behind Axie Infinity, received help from the Axie DAO validator during a period of high transaction volume. Sky Mavis was allowed to sign certain transactions on the DAO’s behalf.

**December 2021:** The temporary arrangement ended, but the permission allowing proxy signing was not removed. Ronin later identified this lingering permission as a key part of the incident.

**23 March 2022:** Attackers used compromised validator keys to authorize fraudulent withdrawals. Ronin reported the stolen amount as 173,600 ETH and 25.5 million USDC.

**29 March 2022:** The incident was discovered after a user could not withdraw 5,000 ETH. Ronin announced the breach and suspended bridge deposits and withdrawals while investigating. The unauthorized transactions had therefore gone undetected for six days.

**6 April 2022:** Japan’s Financial Services Agency’s later incident review records Sky Mavis raising $150 million from investors to help cover the losses.

**14 April 2022:** The FBI publicly attributed the attack to Lazarus Group, a cyber actor associated by U.S. authorities with North Korea. This is an official law-enforcement attribution, not a fact users could independently determine from transaction records alone.

**28 June 2022:** Ronin announced that the bridge had reopened after one internal and two external audits. The company said user funds were fully backed one-to-one and users had been made whole. It separately noted that 56,000 ETH belonging to the Axie DAO treasury remained undercollateralized pending recovery efforts.

Timeline sources: [Ronin’s official incident alert](https://roninblockchain.substack.com/p/community-alert-ronin-validators), [Japan Financial Services Agency research paper](https://www.fsa.go.jp/en/policy/bgin/ResearchPaper_qunie_en.pdf), [FBI statement](https://www.fbi.gov/news/press-releases/press-release/fbi-statement-on-attribution-of-malicious-cyber-activity-posed-by-the-democratic-peoples-republic-of-korea), and [Ronin’s reopening announcement](https://blog.roninchain.com/p/the-ronin-bridge-is-open-).

## Root cause

Ronin’s account says attackers gained control of five of the nine validator keys: four associated with Sky Mavis and one associated with the Axie DAO. Because five approvals were enough, the attacker could authorize withdrawals the bridge treated as valid. The lingering proxy-signing permission helped make the fifth approval possible after Sky Mavis’s own validators were compromised.

The evidence points to a combination of compromised keys and weak permission management, rather than proof that the bridge’s code alone was defective. A multi-approval system only protects users when approvals are controlled independently, permissions are reviewed, and suspicious withdrawals are detected quickly. This explanation describes the system failures documented by Ronin; it does not require assigning unsupported personal blame.

## Amount affected

Ronin reported **173,600 ETH and 25.5 million USDC** stolen. USDC is a stablecoin designed to track the U.S. dollar, while ETH is Ethereum’s native cryptocurrency. The Japan Financial Services Agency’s review valued the loss at approximately **$620.1 million** at the time; other contemporary reports used figures around $625 million. These differences reflect valuation timing and methodology, so the token quantities are the most precise way to describe what was taken.

The 56,000 ETH associated with the Axie DAO treasury was later discussed separately by Ronin. The company said users had been made whole when the bridge reopened, but that should not be confused with proof that every stolen token had been recovered from the attacker.

## What users could and could not do

Ordinary users could not prevent the validator keys from being compromised, reverse completed blockchain transactions, or independently repair the bridge. Once the service was paused, they could not simply force a withdrawal. Those were responsibilities of the operators and their incident-response partners.

Users could, however, reduce exposure before and during an incident. Before depositing, they could investigate who controlled the bridge, read security announcements, and avoid keeping more assets in a bridge than necessary. During the outage, they could stop initiating transfers, monitor official status updates, and beware of fake recovery links or strangers asking for seed phrases. Still, users who already had funds in the bridge could be affected despite taking reasonable precautions.

## What changed afterwards?

Ronin said it raised the withdrawal approval threshold from five to eight validators and strengthened its security controls. When the bridge reopened on 28 June, it reported one internal and two external audits, one-to-one backing for user funds, and repayment of users. The company also described a circuit breaker, a control designed to pause unusually large withdrawals for review. These measures address some weaknesses exposed by the incident, but audits and new controls cannot guarantee that a service will never be compromised again.

## Three checks before trusting a similar service

1. **Check who controls approvals.** Look for the number of validators or signers, how many must approve withdrawals, and whether they are genuinely independent. Nine signers provide less protection if one organization effectively controls most of them.

2. **Read audits and incident disclosures.** Look for dated audits and learn what they cover. Check whether the service explains emergency pauses, permission revocation, monitoring, and how it communicates incidents. An audit is useful evidence, not a guarantee.

3. **Understand the exit route and limit exposure.** Check withdrawal status and limits before depositing. Consider a small test transfer when appropriate, and avoid assuming that successful deposits mean withdrawals are safe. Keep only the amount you need in the service and use verified official channels for updates.

## Sources

1. Ronin, [“Community Alert: Ronin Validators Compromised”](https://roninblockchain.substack.com/p/community-alert-ronin-validators), March 2022. Official incident notice.
2. Ronin, [“The Ronin Bridge Is Open”](https://blog.roninchain.com/p/the-ronin-bridge-is-open-), 28 June 2022. Official reopening and remediation statement.
3. Japan Financial Services Agency, [research paper on the Ronin Network bridge theft](https://www.fsa.go.jp/en/policy/bgin/ResearchPaper_qunie_en.pdf). Incident timeline and loss valuation.
4. The Record, [“More than $625 million stolen in DeFi hack of Ronin Network”](https://therecord.media/more-than-625-million-stolen-in-defi-hack-of-ronin-network), 29 March 2022. Contemporary independent reporting.
5. FBI, [statement attributing malicious cyber activity to North Korea](https://www.fbi.gov/news/press-releases/press-release/fbi-statement-on-attribution-of-malicious-cyber-activity-posed-by-the-democratic-peoples-republic-of-korea), 14 April 2022. Official attribution.

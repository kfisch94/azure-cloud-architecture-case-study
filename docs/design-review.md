# Architecture review

## Source record

The historical sources are my `KyleFischer Cloud Proposal.docx`, `Kyle Fischer- Cloud Proposal Quote.xlsx`, and `Topology Cloudd.PNG` from CMPS-368 coursework. The proposal carries October 2023 dates; the quote is dated November 2, 2023. The topology is reproduced as `assets/original-topology.png`.

The client and consultancy were academic scenario names. Contact details, commercial terms, and the original documents are omitted from this public selection. The instructor's assignment requirements are context, separate from evidence of my results.

## Original design and retrospective findings

This review was prepared for the portfolio in October 2026. It records issues in the historical proposal; it does not represent changes implemented in an Azure environment.

| Topic | Original record | Review finding |
|---|---|---|
| Region choice | Canadian regions in early sections; US West primary and Canada East recovery in later sections | Select one consistent regional design and explicitly identify where each service stores data. The record does not substantiate a compliance guarantee. |
| Identity | Azure Active Directory described for cloud identity; pricing reference points to managed domain services | Clarify the authentication and legacy-domain requirements before choosing products or assigning costs. |
| Storage | Personal storage, shared files, premium storage, archive terminology, and a 1,000 TiB estimate | Separate personal files, shared-file workloads, and archive objects. Establish capacity, growth, throughput, and retention assumptions. |
| Redundancy | GRS recovery descriptions alongside an LRS storage estimate | Reconcile redundancy choices and regional availability with the actual storage product. |
| Applications | Premium App Service in one section; Standard in the pricing section; managed services plus 15 VMs | Choose a consistent service tier and give each VM a distinct workload purpose. Check for duplicate capacity. |
| SQL | 200 GB scenario requirement; pricing discussion uses 1,000 GB | Explain headroom and growth assumptions or revise the sizing. |
| Connectivity | VPN and ExpressRoute described as encrypted transfer options | Specify routing and encryption separately. |
| Recovery | RPO 12 hours and RTO 2 hours | Treat these as targets until backup schedules, dependencies, restoration steps, and tests demonstrate them. |
| Schedule | Approximately 44 weeks; listed phases skip weeks 24–29 | Complete the missing phase and dependencies before treating the schedule as executable. |

## Technical reference checks

Microsoft Entra ID and Microsoft Entra Domain Services serve different identity requirements. Domain Services adds managed traditional domain capabilities such as LDAP and Kerberos/NTLM. The original proposal's cloud identity description and domain-services pricing reference need reconciliation. [Microsoft identity comparison](https://learn.microsoft.com/en-us/entra/identity/domain-services/compare-identity-solutions).

Azure Files uses SSD or HDD file-share offerings, with redundancy support depending on the offering. The original premium-file, archive, and geo-redundancy terminology must be separated into supported product choices; archive access tiers belong to Blob Storage. [Azure Files planning](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-planning), [Blob access tiers](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview).

ExpressRoute traffic is not encrypted by default. A private connectivity choice alone does not establish encryption; the design needs an explicit encryption mechanism. [ExpressRoute encryption](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-about-encryption).

These references were reviewed on October 9, 2026. They support this retrospective review rather than a claim that all current service capabilities were present in the 2023 design.

## Validation before implementation

1. Confirm workload inventory, dependencies, identity requirements, access patterns, and measured storage demand.
2. Select consistent regions, service tiers, network paths, and backup arrangements.
3. Rebuild the cost model with explicit currency, billing periods, commitments, usage assumptions, and migration costs.
4. Run a limited pilot covering sign-in, authorized file access, application-to-database access, and monitoring.
5. Perform restoration and recovery exercises, recording elapsed time and data age against the RTO and RPO targets.
6. Establish migration acceptance criteria, rollback steps, support ownership, and knowledge transfer.

These are proposed next steps, not completed tests.

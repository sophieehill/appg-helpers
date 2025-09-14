# ReadMe

This repo contains lookup tables to help identify UK All Party Parliamentary Groups (APPGs) across different registers. The APPG register data is notoriously messy and the same APPG may appear under various names.

Please report any errors by submitting an issue here or [contacting me](https://www.sophie-e-hill.com/).

[Official parliamentary APPG register](https://www.parliament.uk/mps-lords-and-offices/standards-and-financial-interests/parliamentary-commissioner-for-standards/registers-of-interests/register-of-all-party-party-parliamentary-groups/) 

[Parallel Parliament page on APPGs](https://www.parallelparliament.co.uk/APPGs) (this is helpful because it aggregates information from multiple filings under the same name)

`appg_matching_names.csv` is a CSV file where each row corresponds to a unique APPG entity:

- `name_1` is the name of the APPG entity on its most recent filing (as of September 2020)
- `name_2`, `name_3`, etc. are other names under which that entity has updated the parliamentary register

Out of 1,444 APPGs listed on the Parallel Parliament website (based on official filings since 2015), I identify 1,272 unique entities. There are 322 APPG duplicate names that correspond to 150 unique entities. 

## Defining APPG Continuity

There are lots of easy cases where the APPG chair/officers/purpose/secretariat are the same and there's just a minor name variation: 

- e.g. "Taxis and Private Hire Vehicles APPG" is the same entity as "Taxis APPG"

Others are less obvious: 

- e.g. "Post-Brexit Funding for Nations, Regions and Local Areas APPG" was renamed "UK Shared Prosperity Fund APPG"

Matching was done manually, by checking similarities in:

- APPG name
- APPG purpose (a field on the register)
- APPG officers
- APPG secretariat, public enquiry point, external donors, external website
- Dates between APPG filings (simultaneous filings indicate different entities; sequential filings consistent with one entity changing name)

Note: Sometimes an APPG dissolves and one with a similar purpose is created at a later time. These would _not_ be matched as the same entity unless there was some underlying organisational continuity (e.g. overlapping officers, secretariat). However, APPGs often do not properly disclose ties to external organisations on the register, so this continuity may be inferred indirectly (e.g. from an identical substantive entry in the purpose field or from other contextual information outside the register).

Example:

1. "Excluded UK APPG" registered once 07/08/2020, chair Jamie Stone MP, public enquiry point "sonali@excluded.org", no secretariat listed
    * Purpose: "To find solutions for those who have been excluded from Government Support Schemes during the Coronavirus pandemic."
2. "Gaps in Support APPG", registered 2020-22, chair Jamie Stone MP, secretariat Best for Britain (2020-21)
    * Purpose: "To find solutions for those who have been excluded from Government Support Schemes during the Coronavirus pandemic."
3. "Gaps in Covid-19 Financial Support APPG", registered 2025, chair Steve Witherden MP, secretariat Excluded UK
    * Purpose: "To acknowledge the challenges faced by UK taxpayers excluded from government financial support during the Covid-19 pandemic, to address the failings of past provisions, and to develop equitable solutions ensuring no one is excluded from support in future crises."

(1) and (2) have the same chair, identical purpose, and sequential dates BUT different names and different external orgs (Excluded UK, Best for Britain). (2) and (3) have similar names, but different chair, different external orgs, and a time gap between registers. (1) and (3) have same external org, but different name, different chair, and long time gap.

My coding: (1) and (2) are the same. (3) is considered a distinct entity.

## Rule Change 2024

From March 2024, the rules on APPG registration were changed so that all APPGs had to have exactly 4 officers and MPs could only be officers of a maximum of 6 APPGs. This lead to a significant reduction in the number of APPGs registered. It also caused some APPGs with overlapping memberships to merge into one entity (e.g. "Switzerland & Lichtenstein APPG"). Many APPGs effectively reformed as "Parliamentary Liaison Groups" to avoid additional requirements on reporting donations.

## False Friends

There are also some "false friends", i.e. APPGs with similar names that are actually distinct entities (sometimes with opposing viewpoints!). See: `appg_distinct_names.csv` 

Examples:

- "Armed Forces APPG" is NOT the same as "Armed Forces Community APPG"
- "Football APPG", "Football Club APPG", "Football Supporters APPG" are all different entities
  





***Report on Key Feedback for Data Assessment for UNICEF Activity File – Albania:***

After evaluating the [UNICEF Activity File - Albania](https://iatiregistry.org/dataset/unicef-albania), three key feedback points were identified using the [IATI Validator](https://validator.iatistandard.org/report/unicef-albania) and [IATI CoVE](https://iati.cove.opendataservices.coop/) tools.

Each feedback item highlights a specific aspect of data accuracy and following the IATI Standard (Version 2.02):



**1. Budget Status Validation:**


The first feedback is about an invalid budget status, specifically using an empty space ("") for the @status attribute in the <budget> element:

Error: The budget status is invalid.
"" is not a valid value for attribute @status, in element <budget>


According to the [IATI Activity Standard Summary Table](https://iatistandard.org/en/iati-standard/202/activity-standard/summary-table/) and [IATI reference page for the XML element <budget>](https://iatistandard.org/en/iati-standard/202/activity-standard/iati-activities/iati-activity/budget/#iati-activities-iati-activity-budget-status), the Budget @status indicates whether the reported budget is indicative: Code 1, or formally committed: Code 2.

This attribute value must be a specific type of text (number) and follow the [Budget Status codelist](https://iatistandard.org/en/iati-standard/202/codelists/budgetstatus/).
If there is an empty space and the @status attribute value is not present, the budget is assumed to be indicative and should be given the Code/number 1 accordingly.

**2. Activity Scope Code Validation:**

The second feedback points out an invalid activity scope code, specifically using "Yes" and “NO” for the @code attribute in the <activity-scope> element:

Error: The activity scope code is invalid.
"Yes" and “NO” are not valid values for attribute @code, in element <activity-scope>

The [IATI Activity Standard Summary Table](https://iatistandard.org/en/iati-standard/202/activity-standard/summary-table/) and [IATI Standard Reference for activity-scope](https://iatistandard.org/en/iati-standard/202/activity-standard/iati-activities/iati-activity/activity-scope/#iati-activities-iati-activity-activity-scope-code), emphasise that the @code attribute value should be a particular type of text and match the [Activity-Scope codelist](https://iatistandard.org/en/iati-standard/202/codelists/activityscope/), which includes codes (numbers) from 1 to 8.

**3. Identifier Format Compliance:**

The third feedback highlights a Ruleset error related to the format of identifiers. The identified issue is that the identifier/text() does not match a specific pattern:

Ruleset: Elements must use a valid format.
Rule: identifier/text() should match the regex [^\:\&\|\?]+

According to the [IATI Activity Standard Summary Table](https://iatistandard.org/en/iati-standard/202/activity-standard/summary-table/) and [IATI Standard Reference for Creating IATI activity identifiers](https://iatistandard.org/en/guidance/standard-overview/preparing-your-data/activity-information/creating-iati-identifiers/), a globally unique identifier for each activity must be unique, free from leading or trailing spaces, and composed solely of numbers, letters, and dashes.

***Testing in Jupyter Notebook:***

All above identified changes were thoroughly tested in a Jupyter Notebook within VSCode using Python and is available at this GitHub repository for your reference. This testing process included validating the edited activities using the IATI Validator and ensuring that the corrections meet the IATI Standard.

***Recommendations for Improvement:***

**1. Budget Status:**

o Ensure the @status attribute in the <budget> element is either a valid text from the [Budget Status codelist](https://iatistandard.org/en/iati-standard/202/codelists/budgetstatus/) or omitted to indicate an indicative budget with Code 1.

o Please note that according to the [IATI codelist management guidance](https://iatistandard.org/en/iati-standard/upgrades/how-we-manage-the-standard/codelist-management/#:~:text=Core%20Codelists%20contain%20codes%20that,publishing%20and%20using%20IATI%20data.), this is a Core Codelist, and changing them has a big on impact on all those publishing and using IATI data. Core Codelists contain codes that involve functional logic that impacts the way in which the Standard is interpreted and processed.

**2. Activity Scope Code:**

o Correct the @code attribute in the <activity-scope> element to align with the [Activity-Scope codelist standard](https://iatistandard.org/en/iati-standard/202/codelists/activityscope/), using values from 1 to 8.

o The geographic scope of activity is a Non-Core codelist. Refer to [IATI codelist management guidance](https://iatistandard.org/en/iati-standard/upgrades/how-we-manage-the-standard/codelist-management/#:~:text=Core%20Codelists%20contain%20codes%20that,publishing%20and%20using%20IATI%20data.) for more information.

**3. Identifier Format:**

o Review and modify identifiers to match a specific pattern highlighted in [IATI Standard Reference for Creating IATI activity identifiers](https://iatistandard.org/en/guidance/standard-overview/preparing-your-data/activity-information/creating-iati-identifiers/). Ensure uniqueness, absence of spaces, and use only alphanumeric characters and dashes.

o Note: The provided regex pattern [^\:\&\|\?]+ in IATI Validator is designed to match strings that do not contain colons, ampersands, pipes, or question marks. While this satisfies part of the rule set in the IATI Standard Reference for Creating IATI activity identifiers, it does not explicitly ensure that the identifier only contains numbers, letters, and dashes or that it doesn't start or end with whitespace. To address all the specified rules, I used this regex pattern ^[a-zA-Z0-9]+(?:-[a-zA-Z0-9]+)\*$ to ensures that the identifier starts with a letter or number, followed by an optional sequence of hyphen-separated letters or numbers. It also ensures that the identifier does not start or end with whitespace.

These recommendations aim to improve data quality and conform to the IATI Standard. Following these standards ensures that the data is consistent, accurate, and can be effectively used for analysis.

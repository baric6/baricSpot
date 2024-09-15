# Exchange Create incident reports

## Create incident reports for DLP policy detection

{% embed url="https://learn.microsoft.com/en-us/exchange/create-incident-reports-for-dlp-policy-detections-exchange-2013-help" %}

## Top domain mail-flow status report in the new Exchange admin center in Exchange Online

{% embed url="https://learn.microsoft.com/en-us/exchange/monitoring/mail-flow-reports/mfr-top-domain-mailflow-status-report" %}

## Prevent credit card data from leaving the company

{% embed url="https://subscription.packtpub.com/book/programming/9781838551230/4/ch04lvl1sec50/creating-a-mail-flow-rule" %}

## Creating a mail flow rule <a href="#idparadest-231" id="idparadest-231"></a>

While users can create their own rules to apply to messages upon delivery, mail flow rules set by administrators take effect on messages in transit before they're delivered. In this recipe, we'll create a mail flow rule to help identify and report outgoing mail containing credit card numbers.

Important note

Mail flow rules are also known as transport rules.

### Getting ready <a href="#idparadest-232" id="idparadest-232"></a>

You should be a global admin or have the Organization Management role as part of your assigned permissions to be able to complete the steps in this recipe.

### How to do it… <a href="#idparadest-233" id="idparadest-233"></a>

1. Go to the classic Exchange admin center at https://outlook.office.com/ecp/.
2. Select **mail flow** from the left-hand side navigation menu.
3.  Choose the plus sign (**+**) to create a new rule:

    Figure 4.31 – The plus button for creating a new rule
4. In this recipe, we'll select **Generate an incident report when sensitive information is detected**

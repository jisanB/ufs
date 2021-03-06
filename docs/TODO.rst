µFS TODO
========


Continuously
~~~~~~~~~~~~
- Update Norwegian translation. Last done 2008-04-10
- Write/update documentation
- Write/update unit tests
- Test use cases
- egrep -ir 'todo|fixme|xxx' itkufs/


ACCOUNTING
----------

This release
~~~~~~~~~~~~
- Use cases:
	- Check status of bar economy
	- Register sales to own users
	- Register sales to other groups
	- Print new lists
	- Settlement
		- Create new
		- Register recievables
		- Register payments
- Use decorators to control commit/rollback of transactions. At least in all
  views which has to do with transactions. Check possible Django bug :(
- Transaction list and approve transaction view should resemble each other.
- Owner can't access reject transaction for his own deposits and transfers
- Change properties to transaction manager methods where it makes sense (ask adamcik)
  some of the helpers that we have defined as properties on the model should probably
  be Manager methods instead

Nytt 2008-09-08
- Ta i bruk generic_create/update
- Ta i bruk formset_factories (still missing for new transaction, perhaps not a
  good switch there)
- Ta i bruk objektorientert pagination

Nytt 2008-09-25
- bsf wizzard
- utlegg skjema

Done
~~~~
*lots*
- (adamcik) Assign AccountRoles.
- (adamcik) cron nag mail

Wontfix
~~~~~~~
- set_rejected() must enforce who is allowed to alter state. A user may reject
  his withdrawal or deposit if state=pending. An admin may reject everything if
  state=pending.
- group,is_admin,account,is_owner context processor (request does not seem to
  contain enough data to do this)

Later release
~~~~~~~~~~~~~
- Date based transaction lists. Filter on account and settlement.
- Mail users when:
	- Balance is below warning limit
	- Balance is below block limit
	- Participant in transaction which is rejected
- Create pre-populated correction transactions.
- 'New claim' as an action for regular users to claim expenses from each other
  or from the group.


REPORTS
-------

This release
~~~~~~~~~~~~
- More interesting submenu.
- Modify Account.balance() to return the balance at a given date, then modify
  the balance and income statements so that one can specify for which date you
  want the report to be valid. (partialy implmeneted, not done in SQL and we still
  need something smart for graphs)
- Review code
- Write unit tests
- Write documentation

Later release
~~~~~~~~~~~~~
- Pie chart of balance statement
- Bar chart of income statement
- Line chart of developments through time

Even later release
~~~~~~~~~~~~~~~~~~
- Private (for the user himself) high score of where the user spends the most
  money


INVOICING
---------

Later release
~~~~~~~~~~~~~
- Creating invoices for other groups, either for email or printing.
- A standardized setup would probably be beneficial.
- Start out with just name of spender, amount and sum.

Even later release
~~~~~~~~~~~~~~~~~~
- Cache names in the DB and use JavaScript to fetch them on the fly.
- Use user names from other groups, if they use µFS.


INVENTORY
---------

Later release
~~~~~~~~~~~~~
- A catalog of articles with quantity and price
- Support the purchase workflow:
	1. User/admin registers purchase of new/more articles
	2. Admin approves purchase
	3. Admin decides prices for new articles and updates for old
	4. User/admin prints price list
- Support the catalog update workflow:
	1. User/admin/slave counts the quantity of all articles
	2. Admin updates the catalog with the new quantities

Even later release
~~~~~~~~~~~~~~~~~~
- µFS helps the admin decide reasonable prices, given estimates on loss
- µFS helps the admin improve the loss estimates based on inventory counts and
  sales reports


..
    vim: ft=rst tw=74 ai

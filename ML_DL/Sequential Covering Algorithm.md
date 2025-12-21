[[Machine Learning]]

A set of rules is learned one at a time, 

each time finding a single rule that covers a large number of positive instances without covering any negatives,

removing the positives that it covers, and learning additional rules to cover the rest.

`Let P be the set of positive examples`
`Until P is empty do:`
	``Learn a rule R that covers a large number of elements of P ``
	`but no negatives.`
`Add R to the list of rules.`
`Remove positives covered by R from P`

•This is an instance of the greedy algorithm for minimum set covering and does not guarantee a minimum number of learned rules.

•Minimum set covering is an NP-hard problem and the greedy algorithm is a standard approximation algorithm.

•Methods for learning individual rules vary.

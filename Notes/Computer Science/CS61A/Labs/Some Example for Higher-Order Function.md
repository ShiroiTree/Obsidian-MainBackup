```
def say_scores(score0, score1):
	"""A commentary function that announces the score for each player."""
	print("Player 0 now has", score0, "and Player 1 now has", score1)
	return say_scores
```

```
def announce_lead_changes(last_leader=None):
	"""Return a commentary function that announces lead changes.
	>>> f0 = announce_lead_changes()
	>>> f1 = f0(5, 0) 
	Player 0 takes the lead by 5
	>>> f2 = f1(5, 12) 
	Player 1 takes the lead by 7
	>>> f3 = f2(8, 12)
	>>> f4 = f3(8, 13)
	>>> f5 = f4(15, 13)
	Player 0 takes the lead by 2 """ 
	def say(score0, score1):
		if score0 > score1:
			leader = 0
		elif score1 > score0:
			leader = 1
		else:
			leader = None
		if leader != None and leader != last_leader:
			print('Player', leader, 'takes the lead by', abs(score0 - score1))
		return announce_lead_changes(leader)
	return say
```

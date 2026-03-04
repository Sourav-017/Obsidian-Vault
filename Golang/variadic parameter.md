[[GOLANG]] [[go_functions]]
func CalculateTotals(playerScores ...[]int) []int {
	totals := make([]int, len(playerScores))
	for i, scores := range playerScores {
		totals[i]=CalculateTotal(scores)
	}
	
	return totals
}

- `...[]int` means "accept any number of []int arguments" (variadic parameter)
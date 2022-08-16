# leetcodesolutions
My leetcode solutions 

# Two City Scheduling

class Solution:
    def twoCitySchedCost(self, costs: List[List[int]]) -> int:
        cityA = 0
        cityB = 0
        total = 0
        equal = 0
        
        diff = []
        
        for pair in costs:
            diff.append(pair[1] - pair[0])
            total = total + min(pair)
            if pair[0] == pair[1]:
                equal = equal + 1
            elif min(pair) == pair[0]:
                cityA = cityA + 1
            elif min(pair) == pair[1]:
                cityB = cityB + 1

        if equal == len(costs):
            return total
        if equal > 0:
            print("equals, ", equal)
            print(cityA, cityB)
            if cityA > cityB:
                cityB = cityB + equal
            else: 
                cityA = cityA + equal
            print("equals ", cityA, cityB)
            for i in range(equal):
                diff.remove(0)
        print(diff)
        print(total)

       
        while cityA !=cityB:
            print(cityA, cityB)
            if cityB > cityA:
                smallest = max([i for i in diff if i < 0])
                total = total + abs(smallest)
                diff.remove(smallest)
                cityB = cityB - 1
                cityA = cityA + 1
            else:
                total = total + min([i for i in diff if i > 0])
                diff.remove(min([i for i in diff if i > 0]))
                cityB = cityB + 1
                cityA = cityA -1
                
            
        return total 

[[GOLANG]]


```package main

import "fmt"

func main() {
    // Original map
    phonebook := map[string]string{
        "John": "0123456789",
        "Bob":   "0987654321",
    }

    // Copy the map (both point to SAME underlying data)
    copy := phonebook

    // Modify via "copy"
    copy["Alice"] = "0555555555"     
    copy["John"] = "1111111111"     
    delete(copy, "Bob")            

    // Check original - IT CHANGED TOO!
    fmt.Println("Original phonebook after modifying copy:")
    fmt.Println("John:", phonebook["John"])   // Output: 1111111111 (changed!)
    fmt.Println("Bob:", phonebook["Bob"])       // Output: (empty - deleted!)
    fmt.Println("Alice:", phonebook["Alice"])   // Output: 0555555555 (added!)

    // Both variables see the same changes
    fmt.Println("\nBoth point to same data:")
    fmt.Printf("phonebook: %v\n", phonebook)
    fmt.Printf("copy:      %v\n", copy)
}
**copy also changes when the original map is changed**

number, exists := phonebook["Unknown"] 
if exists { 
	fmt.Println("Found:", number) 
} 
else { 
	fmt.Println("Not found!") 
}
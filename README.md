# Election_Analysis
## Overview 
In the Election Analysis project we were tasked with analysing election results to determine the participating counties, candidate outcomes and the winning candidate vote counts. 
## Election Audit Results 
* By creating the following for loop we were able to determine the total votes casted: 369,711

```
for row in reader:

        total_votes = total_votes + 1

```

* The following code allows us to print the details below that provide us with the county breakdown. 

```
with open(file_to_save, "w") as txt_file:
   
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    for key, values in county_votes.items ():
        percentage = round(values / total_votes *100, 1)
        line = key + ": " + str(percentage) + "%" + " (" + str(total_votes) + ")" + "\n"
        election_results += line 
    election_results += f"-------------------------\n\n"
    print(election_results, end="")

    txt_file.write(election_results)
    
 ```
![County_Results](C:>Users>jesse>OneDrive>Desktop>Data Analysis>County_Results.PNG). 

* We were also able to determine the candidate details and winner by using the following code:

```
for candidate_name in candidate_votes:

        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        print(candidate_results)

        txt_file.write(candidate_results)

        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage
  
```
![Candidate_Details]((OneDrive\Desktop\Data Analysis\Candidate_Details.png). 

## Election Audit Summary 
The for loops and if conditions that were used in this script could be used as a base for any election. It simply loops through the various counties and candidates pulling the data that's needed to analyze the results. 


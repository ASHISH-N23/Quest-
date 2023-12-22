#!/usr/bin/env bash

# Exercise 1: Find all ships that appeared in Return of the Jedi
clear
URL='https://swapi.dev/api'
n=1

while true
do
	response=$( curl -sL -H 'Accept: application/json' ${URL}/films?page=${n} )
	if [[ ${response} =~ .*detail.*Not.* ]]; then
		break
	fi
	# echo $response | jq .
	# logic
	RESULTS=`echo $response | jq '.results[] | select(.title=="Return of the Jedi").starships'`
	COUNTER=`echo $response | jq '.results[] | select(.title=="Return of the Jedi").starships' | jq length`
	for i in $(seq 0 $COUNTER); 
	do 
		# echo $COUNTER
		SUB_URL=`echo $RESULTS | jq -r .[$i]`
		# echo $SUB_URL
		curl -sL -H 'Accept: application/json' ${SUB_URL} | jq ".name"
	done
	n=$((n + 1))
done
# echo ${n}

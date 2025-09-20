#!/usr/bin/env bash
# This script displays all active IPv4 addresses on the machine

# Use the ifconfig and grep to filter out IPv4 addresses
ifconfig | grep -w "inet" | awk '{print $2}'

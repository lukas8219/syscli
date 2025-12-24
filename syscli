#!/bin/bash

# Parse command line arguments
RESOURCE=""
TYPE=""

while [[ $# -gt 0 ]]; do
    case $1 in
        --resource)
            RESOURCE="$2"
            shift 2
            ;;
        --type)
            TYPE="$2"
            shift 2
            ;;
        *)
            echo "Unknown option: $1"
            echo "Usage: $0 [--resource <resource>] [--type <type>]"
            exit 1
            ;;
    esac
done

# Get the directory where the script is located
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
CSV_FILE="$SCRIPT_DIR/dataset"

# Check if dataset file exists
if [[ ! -f "$CSV_FILE" ]]; then
    echo "Error: dataset file not found in $SCRIPT_DIR"
    exit 1
fi

# Read and process the CSV file
{
    # Read the header
    IFS=',' read -r col1 col2 col3 col4
    # Output header with proper alignment
    printf "%-25s %-15s %-30s %-s\n" "$col1" "$col2" "$col3" "$col4"

    # Process data rows
    while IFS=',' read -r resource type command description; do
        # Apply filters if specified
        if [[ -n "$RESOURCE" && "$resource" != "$RESOURCE" ]]; then
            continue
        fi
        if [[ -n "$TYPE" && "$type" != "$TYPE" ]]; then
            continue
        fi

        # Remove quotes from command and description
        command="${command//\"/}"
        description="${description//\"/}"

        # Output row with proper alignment
        printf "%-25s %-15s %-30s %-s\n" "$resource" "$type" "$command" "$description"
    done
} < "$CSV_FILE"

#!/bin/sh

# APT Search Engine
# Requires apt-cache (available on Debian, Ubuntu, and many APT-based derivatives).

credit='Author BLACKREAPER38 on GitHub'

printf '%s\n' '=================' 'APT Search Engine' '=================' ''

if ! command -v apt-cache >/dev/null 2>&1; then
    printf '%s\n' 'Error: apt-cache was not found.' \
        'This script requires an APT-based system, such as Debian or Ubuntu.' >&2
    exit 1
fi

while :; do
    printf '%s\n' '1. Search' '2. Exit' ''
    printf 'Choose an option: '

    if ! IFS= read -r choice; then
        printf '\n%s\n' "$credit"
        exit 0
    fi

    case $choice in
        1)
            printf 'Enter package name or search term: '
            if ! IFS= read -r package_name; then
                printf '\n%s\n' "$credit"
                exit 0
            fi

            if [ -z "$package_name" ]; then
                printf '%s\n\n' 'Please enter a search term.'
                continue
            fi

            printf '\nSearch results for: %s\n\n' "$package_name"
            apt-cache search -- "$package_name"
            printf '\n'
            ;;
        2)
            printf '%s\n' "$credit"
            exit 0
            ;;
        *)
            printf '%s\n\n' 'Invalid option. Enter 1 or 2.'
            ;;
    esac

done

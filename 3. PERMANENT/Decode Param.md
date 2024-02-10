---
type: evidence
topic: bash 
---
- Topic : #bash
- Tags : #linux #dev 

# Idea

Better handling function parameters and script arguments in bash by allowing to use the following arguments calls:
- -t
- --tag test

## Script 

```bash
#--------------------------------------------------------
# Handle Named Parameters
# Usage : eval "declare -A params=$(decode_params "$@")"
#--------------------------------------------------------

function decode_params() {
    # Declare a variable to hold the named parameters
    declare -A params

    local i=0

    # Loop through the input arguments
    while [[ $# -gt 0 ]]; do
        case "$1" in
        # If the argument starts with "--", it is a named parameter
        --*)
            # Split the argument on the "=" character to separate the name and value
            name=$1
            value=$2
            # Check if value 2 is not empty and does not start with "--"
            if [[ -n "$2" ]] && [[ ! "$2" =~ ^--.* ]]; then
                # If it is not empty and does not start with "--", then it is the value
                value=$2
                # Shift the arguments so that the next iteration will use the next argument as the value
                shift
            else
                # If it is empty or starts with "--", then it is an empty string
                value=""
            fi
            # Store the name and value in the params array
            params[$name]=$value
            shift
            ;;
        # If the argument starts with a single "-", it is a boolean flag
        -?)
            # Store the name and value in the params array
            params[$1]="true"
            shift
            ;;
        # If the argument doesn't start with "--" or with a single "-", it is a regular argument
        *)
            # Store the argument in the "regular_args" array
            value=$1
            i=$((i + 1))
            name="$i"
            params[$name]=$value
            shift
            ;;
        esac
    done

    local result="("
    for key in "${!params[@]}"; do
        result+="[$key]=\"${params[$key]}\" "
    done
    result+=")"

    echo "$result"
}
```

## Usage


```Bash
	# Decode parameters
    eval "declare -A params=$(decode_params "$@")"

    # Check if mandatory parameters are set
    if [[ -z "${params[--acron]}" || \
            -z "${params[--template-path]}" || \
            -z "${params[--destination-path]}" || \
            -z "${params[--sst-name]}" || \
            -z "${params[--sst-email-service-adherent]}" || \
            -z "${params[--sst-siret-enable]}" || \
            -z "${params[--sst-tiers-declarant-enable]}" || \
            -z "${params[--code-orga-paterne]}" || \
            -z "${params[--code-orga-tooltip]}" || \
            -z "${params[--mail-display-name]}" || \
            -z "${params[--sms-enable]}" ]]; then
        insertOrgaInSymfonyParametersConfigFileEnv_usage
    fi

    # Set parameters
    ACRON="${params[--acron]}"
    TPLPATH="${params[--template-path]}"
    DESTPATH="${params[--destination-path]}"
    SST_NAME="${params[--sst-name]}"
    SST_PHONE="${params[--sst-phone]}"
    SST_EMAIL="${params[--sst-email]}"
    SST_EMAIL_SERVICE_ADHERENT="${params[--sst-email-service-adherent]}"
    SST_SIRET_ENABLE="${params[--sst-siret-enable]}"
    SST_TIERS_DECLARANT_ENABLE="${params[--sst-tiers-declarant-enable]}"
    CODE_ORGA_PATERNE="${params[--code-orga-paterne]}"
    CODE_ORGA_TOOLTIP="${params[--code-orga-tooltip]}"
    MAIL_DISPLAY_NAME="${params[--mail-display-name]}"
```

# Links

Sources :

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to write better Bash script that are reusable]]

## South : What does it lead to


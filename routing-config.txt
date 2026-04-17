I worked with Perplexity to generate a routing configuration for Windows and MacOS to orchestrate my paid tools. 

---

Windows Script

Here is the configuration for Windows:

# CreatrWeb — Paid Stack Routing

function creatr {
    param(
        [Parameter(Mandatory=$true)]
        [ValidateSet("scaffold","spec","ui","feature","build","inline","review")]
        [string]$Task,

        [Parameter(Mandatory=$false)]
        [string]$Prompt = ""
    )

    switch ($Task) {
        "scaffold" {
            Write-Host "Routing to Codex CLI (schema, scaffolding, Phase 1)"
            if ($Prompt) { codex $Prompt } else { codex }
        }
        "spec" {
            Write-Host "Routing to Claude Code (IndieWeb specs, security, multi-file)"
            if ($Prompt) { claude $Prompt } else { claude }
        }
        "ui" {
            Write-Host "Routing to Gemini CLI (UI components, client-side features)"
            if ($Prompt) { gemini $Prompt } else { gemini }
        }
        "feature" {
            Write-Host "Routing to Cursor (feature iteration, gallery decisions)"
            Write-Host "Open Cursor in this directory:"
            cursor .
        }
        "build" {
            Write-Host "Routing to Vibe CLI (auto-build, conservative defaults)"
            Write-Host "Review DECISIONS.md after this session."
            if ($Prompt) { vibe $Prompt } else { vibe }
        }
        "inline" {
            Write-Host "Routing to GitHub Copilot (mechanical edits, single-file)"
            Write-Host "Use Copilot inline suggestions in VS Code."
            code .
        }
        "review" {
            Write-Host "Routing to Claude Code (EVAL_PROMPT audit)"
            claude "$(Get-Content EVAL_PROMPT.md -Raw)"
        }
    }
}

Instructions:
1. Open your PowerShell terminal.
2. Open your profile script by running: `code $PROFILE` or `notepad $PROFILE`
3. Copy and paste the above function into your terminal to define the `creatr` function
4. Save the file and restart your terminal or run `source $PROFILE` to load the function.

Usage examples:
> creatr scaffold
> creatr spec "Implement Webmention endpoint"
> creatr ui "Build the search interface"
> creatr build
> creatr review

---

MacOS Script

Here is the configuration for MacOS:

# CreatrWeb — Paid Stack Routing

# CreatrWeb — Paid Stack Routing
creatr() {
    local task=$1
    local prompt=$2

    case "$task" in
        scaffold)
            echo "Routing to Codex CLI (schema, scaffolding, Phase 1)"
            if [ -n "$prompt" ]; then codex "$prompt"; else codex; fi
            ;;
        spec)
            echo "Routing to Claude Code (IndieWeb specs, security, multi-file)"
            if [ -n "$prompt" ]; then claude "$prompt"; else claude; fi
            ;;
        ui)
            echo "Routing to Gemini CLI (UI components, client-side features)"
            if [ -n "$prompt" ]; then gemini "$prompt"; else gemini; fi
            ;;
        feature)
            echo "Routing to Cursor (feature iteration, gallery decisions)"
            echo "Opening Cursor in this directory."
            cursor .
            ;;
        build)
            echo "Routing to Vibe CLI (auto-build, conservative defaults)"
            echo "Review DECISIONS.md after this session."
            if [ -n "$prompt" ]; then vibe "$prompt"; else vibe; fi
            ;;
        inline)
            echo "Routing to GitHub Copilot (mechanical edits, single-file)"
            echo "Use Copilot inline suggestions in VS Code."
            code .
            ;;
        review)
            echo "Routing to Claude Code (EVAL_PROMPT audit)"
            claude "$(cat EVAL_PROMPT.md)"
            ;;
        *)
            echo "Unknown task: $task"
            echo "Valid tasks: scaffold | spec | ui | feature | build | inline | review"
            ;;
    esac
}

Instructions:
1. Open your terminal.
2. Open your shell profile script by running: `code ~/.zshrc` or `code ~/.bashrc`
3. Copy and paste the above function into your terminal to define the `creatr` function
4. Save the file and restart your terminal or run `source ~/.zshrc` or `source ~/.bashrc` to load the function.

Usage examples:
> creatr scaffold
> creatr spec "Implement Webmention endpoint"
> creatr ui "Build the search interface"
> creatr build
> creatr review
# ~/.zshrc

## Config

```zsh
alias czrc='nvim ~/.zshrc'
alias szrc='source ~/.zshrc'
alias cgty='nvim ~/.config/ghostty/config'
alias caty='nvim ~/.config/alacritty/alacritty.toml'

alias tallag='trash ~/.gemini/antigravity/brain/*(N) ~/.gemini/antigravity-cli/brain/*(N) ~/.gemini/antigravity-ide/brain/*(N)'
```

## Network

```zsh
#alias inet='ifconfig | grep "inet " | grep -v 127.0.0.1'
alias inet='echo "Local: $(ipconfig getifaddr en0)" && echo "Public: $(curl -s ifconfig.me)"'
alias tnet='curl -I https://www.google.com'
```

## Print Greek Letters

```zsh
# The Greek alphabet consists of 24 letters
alias pgrk='echo "The Greek alphabet consists of 24 letters" && echo "Uppercase: Α Β Γ Δ Ε Ζ Η Θ Ι Κ Λ Μ Ν Ξ Ο Π Ρ Σ Τ Υ Φ Χ Ψ Ω" && echo "Lowercase: α β γ δ ε ζ η θ ι κ λ μ ν ξ ο π ρ σ τ υ φ χ ψ ω"'
```

## TranslateGemma

```zsh
# TranslateGemma 核心翻译函数（内部共用）
_gemma_translate_core() {
    local src_full="$1"
    local src_code="$2"
    local tg_full="$3"
    local tg_code="$4"
    shift 4
    local text="$*"

    if [ -z "$text" ]; then
        echo "错误: 请提供需要翻译的文本。"
        return 1
    fi

    local prompt="You are a professional ${src_full} (${src_code}) to ${tg_full} (${tg_code}) translator. Your goal is to accurately convey the meaning and nuances of the original ${src_full} text while adhering to ${tg_full} grammar, vocabulary, and cultural sensitivities. Produce only the ${tg_full} translation, without any additional explanations or commentary.

Please translate the following ${src_full} text into ${tg_full}:

${text}"

    ollama run translategemma "$prompt"
}

# TranslateGemma 英译中快捷工具
en2zh() {
    local text
    if [ -z "$*" ]; then
        # 如果没有直接带参数，提示用户输入或粘贴，read 会将整行内容存为纯字符串
        printf "请输入要翻译的英文 (回车确认): \n> "
        read -r text
    else
        text="$*"
    fi
    _gemma_translate_core "English" "en" "Chinese" "zh" "$text"
}

# TranslateGemma 中译英快捷工具
zh2en() {
    local text
    if [ -z "$*" ]; then
        printf "请输入要翻译的中文 (回车确认): \n> "
        read -r text
    else
        text="$*"
    fi
    _gemma_translate_core "Chinese" "zh" "English" "en" "$text"
}
```


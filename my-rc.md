# My .*rc

## Config

```zsh
alias czrc='nvim ~/.zshrc'
alias szrc='source ~/.zshrc'
alias cgty='nvim ~/.config/ghostty/config'
alias caty='nvim ~/.config/alacritty/alacritty.toml'
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
# TranslateGemma 英译中快捷工具
en2zh() {
    if [ -z "$1" ]; then
        echo "错误: 请提供需要翻译的英文文本。"
        return 1
    fi
    local text="$*"
    local prompt="You are a professional English (en) to Chinese (zh) translator. Your goal is to accurately convey the meaning and nuances of the original English text while adhering to Chinese grammar, vocabulary, and cultural sensitivities. Produce only the Chinese translation, without any additional explanations or commentary.

Please translate the following English text into Chinese:

${text}"

    ollama run translategemma "$prompt"
}

# TranslateGemma 中译英快捷工具
zh2en() {
    if [ -z "$1" ]; then
        echo "错误: 请提供需要翻译的中文文本。"
        return 1
    fi
    local text="$*"
    local prompt="You are a professional Chinese (zh) to English (en) translator. Your goal is to accurately convey the meaning and nuances of the original Chinese text while adhering to English grammar, vocabulary, and cultural sensitivities. Produce only the English translation, without any additional explanations or commentary.

Please translate the following Chinese text into English:

${text}"

    ollama run translategemma "$prompt"
}
```


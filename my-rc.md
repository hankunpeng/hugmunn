# My .*rc

## config

```
alias czrc='nvim ~/.zshrc'
alias szrc='source ~/.zshrc'
```

## network

```
#alias inet='ifconfig | grep "inet " | grep -v 127.0.0.1'
alias inet='echo "Local: $(ipconfig getifaddr en0)" && echo "Public: $(curl -s ifconfig.me)"'
alias tnet='curl -I https://www.google.com'
```

## print Greek letters

```
The Greek alphabet consists of 24 letters
alias pgrk='echo "The Greek alphabet consists of 24 letters" && echo "Uppercase: Α Β Γ Δ Ε Ζ Η Θ Ι Κ Λ Μ Ν Ξ Ο Π Ρ Σ Τ Υ Φ Χ Ψ Ω" && echo "Lowercase: α β γ δ ε ζ η θ ι κ λ μ ν ξ ο π ρ σ τ υ φ χ ψ ω"'
```

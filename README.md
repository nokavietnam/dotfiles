## Init

```
git init --bare "$HOME/.dotfiles"

# Thêm alias vào ~/.zshrc
echo "alias dotfiles='/usr/bin/git --git-dir=\$HOME/.dotfiles/ --work-tree=\$HOME'" >> ~/.zshrc

# Nạp lại cấu hình shell
source ~/.zshrc

dotfiles config --local status.showUntrackedFiles no


# Thêm cấu hình ghostty và nvim
dotfiles add ~/.config/ghostty
dotfiles add ~/.config/nvim

# Thêm luôn tmux và zshrc nếu có
dotfiles add ~/.tmux.conf

# Kiểm tra trạng thái
dotfiles status

# Commit
dotfiles commit -m "feat: initial commit for dotfiles (ghostty, nvim, tmux, zsh)"

# Đổi nhánh chính thành main
dotfiles branch -M main

# Thêm remote URL
dotfiles remote add origin git@github.com:<your-username>/dotfiles.git

# Push lên remote
dotfiles push -u origin main

```

## Setup

```
## 1. Khai báo alias tạm thời
alias dotfiles='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'

## 2. Đảm bảo thư mục dotfiles nằm trong danh sách ignore tạm thời để tránh đệ quy
echo ".dotfiles" >> .gitignore

## 3. Clone bare repo về máy
git clone --bare dotfiles remote add origin git@github.com:nokavietnam/dotfiles.git "$HOME/.dotfiles"

## 4. Checkout các file ra $HOME
dotfiles checkout
```

```
## Xử lý xung đột file có sẵn 
mkdir -p .dotfiles-backup && \
dotfiles checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
xargs -I{} mv {} .dotfiles-backup/{}

## Thử checkout lại
dotfiles checkout
```

```
## chạy lại cấu hình ẩn file untracked trên máy mới
dotfiles config --local status.showUntrackedFiles no

``

## 說明

1. 答案直接寫在這個 `mid-term.md` 裡，並使用 Markdown 語法撰寫。
1. 題目總共分 Ruby、Rails 以及 Git 三大主題，請在每個主題完成時進行 Commit。
1. 完成後，請發送 PR 至 `mid-term` 分支。
1. 也就是說，你的 PR 應該只會有三或四次的 Commit。

## Ruby 題目 (50 分)

1. (10 分) 請完成本題實作內容

```ruby
class Cat
  attr_reader :name
  def  initialize(name)
    @name = name
  end
end

kitty = Cat.new("kitty")
puts kitty.name  # 在畫面上印出 kitty 字樣
```

2. (5 分) 假設有個 Hash：

```ruby
profile = {name: "kk", age: 18}
```

當執行這行程式：

```ruby
p profile["name"]
```

會得到什麼結果? 為什麼?

> 會得到一個nil，因為沒有回傳值

3. (5 分) 如果要在 1 到 100 的數字當中，任意取出 5 個不重複的亂數，你會怎麼做？

```ruby
puts [*1..100].sample(5)
```
4. (10 分)
```ruby
class Bank
  def transfer(amount)
    # ...
  end
end

Bank.transfer(10)
```

上面這段程式碼執行後會發生什麼事？為什麼？如果有錯誤又該如何修正？

> 會出現還沒有定義Bank類別中transfer方法的錯誤
```ruby
class Bank
  def initialize(amount)
    @amount = amount
  end
  def transfer
    puts "#{@amount}"
  end
end
iffy=Bank.new(10)
iffy.transfer
```

5. (10 分) 請問以下方法：

```ruby
link_to "刪除", products_path(product), method: :delete, class: "btn btn-default"
```

`link_to` 方法共有幾個參數？為什麼？

6. (10 分) 在 Ruby 裡面常會看到冒號的寫法，例如：

有的冒號靠右邊：

```ruby
class Store
  has_many :products
end
```

有的冒號靠左邊：

```ruby
link_to "檢視", books_path(book), class: "btn btn-default"
```

或是兩邊都有：

```ruby
user_profile = {name: "kk", age: 18, blood_type: :b_negative}
```

請問，這三種寫法分別代表什麼意思呢？

## Rails 題目 (30 分)

1. (10 分) 請簡述 `bundle install` 指令的用途。

> 確保所有套件都有正常安裝（檢查與安裝）


2. (10 分) 請說明 `rails db:migrate` 這個指令的用途是什麼？

> 把 Migration 轉換成真正的表格

3. (10 分) 假設某個 Controller 的程式碼如下：

```ruby
class BooksController < ApplicationController
  def index
    @books = Book.all
  end

  def update
    @book = Book.find_by(id: params[:id])
    @book.update(price: 100)
    redirect_to books_path, notice: "資料更新成功"
  end
end
```

請問：
- 第 3 行的 `@books` 前面的那個 `@` 是什麼意思？如果把 `@` 拿掉會發生什麼事？

> @是將books定義為實體變數，如果拿掉得話會變成區域變數

- 第 7 行以及第 8 行的 `@book`，如果把 `@` 拿掉會發生什麼事？為什麼？
> 拿掉之後就無法在他處進行引用，因為區域變數無法被外部進行存取
## Git 題目 (20 分)

1. (10 分) 在你想像中的分支(branch)，是個什麼樣子的東西?
分支在我的想象中，是一個可以協同不同功能開發的東西，概念上有點像是專案分身術的感覺，而最後也會在要合併功能時回到本體，是個在協同分離製作時的好功能．
1. (5 分) 空的資料夾無法被加入 Git 版控，但如果就是想讓這個資料夾留下來，你會怎麼處理?
我會在裡面建立一個名為 “.keep” 或 “.gitkeep” 的空檔案
2. (5 分) 如果有些檔案，像是 `/config/database.yml` 之類比較機密的檔案，不想放在 Git 裡面，你會怎麼做？
在專案中建立一個 .gitignore的檔案，並加入
/config/database.yml
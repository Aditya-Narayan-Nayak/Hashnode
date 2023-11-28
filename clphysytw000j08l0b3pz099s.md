---
title: "How To fix gopls was not able to find modules"
seoTitle: "How To fix gopls was not able to find modules"
seoDescription: "How to fix gopls was not able to find modules in your workspace.
When outside of GOPATH, gopls needs to know which modules you are working on."
datePublished: Tue Nov 28 2023 06:36:27 GMT+0000 (Coordinated Universal Time)
cuid: clphysytw000j08l0b3pz099s
slug: how-to-fix-gopls-was-not-able-to-find-modules
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701153250825/7ab3cce7-84a3-4b90-a062-877b93be5729.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1701153269761/0354dcd8-9a84-4ec5-a99d-1471f89baaef.jpeg
tags: programming, azure, google, gopls

---

Its very simple. let's start with how to get this error I'm assuming you already have installed go lang in your machine.

### 🚀Step 1:-

Now just go to desktop and create a folder called go lang and open that in VS Code.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701149481811/f86398a0-b1b1-4bd6-96db-808a054532af.png align="center")

### 🚀Step 2:-

Create a folder called cards inside there create main.go and paste the following code given below

```go
package main
import (
	"fmt"
)
func main() {
	// var card string = "Ace of Spades"
	cards := []string{"Ace of Diamonds", newcard()}
	cards = append(cards, "Six of shades")

	for i, card := range cards {
		fmt.Println(i, card)
	}
}
func newcard() string {
	return "Five of Demonds"
}
```

### 🚀Step 3:-

in Golang folder create a file called cs.go and paste the code below

```go
package main
import (
	"fmt"
)
func main() {
	cards := "Ace of shades" 	
	fmt.Println(cards)
}
```

The Folder would look like this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701151654193/7b857b03-54e3-43bd-b5e7-7c8a9cdb41c5.png align="center")

### 🚀Step 4:-

Now open the terminal and in problem you see the error looks like this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701151816112/1ab1e540-de7e-4de0-896c-5b0a09e2c041.png align="center")

### 🚀Step 5: -

Let's fix this. Now go back to the terminal and see your path. and type

```powershell
cd cs
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701152212426/805f5199-208a-4eda-9802-ad6a7926fad0.png align="center")

### 🚀Step 6: -

Now you are in cs directory. Run

```powershell
go mod init cs
```

Save this file CTRL +S. See Error is gone.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701152438228/28c3f167-982f-412d-b317-230ba7e32931.png align="center")

Enjoy and give a red/pink heart if it helps you fix the issue. happy Coding.
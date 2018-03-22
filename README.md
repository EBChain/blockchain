Easyblockchain
==========


Go Client for the Blockchain Data API https://ebchain.in/api/blockchain_api


## Installation

```
go get github.com/ebchain/blockchain
```

## Example

```go
package main

import (
  "github.com/ebchain/blockchain"
  "fmt"
)

func main() {

	c, e := blockchain.New()
	resp, e := c.GetAddress("162FjqU7RYdojnejCDe6zrPDUpaLcv9Hhq")
	if e != nil {
		fmt.Print(e)
	}

	fmt.Println(resp.Hash160)
	fmt.Println(resp.Address)
	fmt.Println(resp.NTx)
	fmt.Println(resp.TotalReceived)
	fmt.Println(resp.TotalSent)
	fmt.Println(resp.FinalBalance)

	for i := range resp.Txs {
		fmt.Println(resp.Txs[i].Result)

		for j := range resp.Txs[i].Inputs {
			fmt.Println(resp.Txs[i].Inputs[j].Sequence)
			fmt.Println(resp.Txs[i].Inputs[j].PrevOut.Spent)
		}
	}

}
```

## License

- 對nand做read會有week program的效果，如果讀取次數過多，會導致nand上的殘留電荷變高並引發bit flip
- 所以FTL必須建立一張表，記錄每個block read的次數並設定閾值
- 當block讀取次數超過閾值時，檢查bit filp的數量
	- 如果很多，就把block的data寫到另一個block
	- 如果不多，就設一個更高的閾值，之後再觀察它的bit file數量
- PE cycle越大的block，閾值要設得越低
	- 因為pe cycle高的block，上面的nand殘留電荷也較多，所以也比較不能承受太多次的讀取
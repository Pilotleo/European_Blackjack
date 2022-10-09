# European_Blackjack
請搜尋檔案中的 看這裡-->就是吃喜酒前的進度
有幾點Guide需要請你幫忙
## 1.
我把p1_sts也丟進去了simulation了，想要知道**怎麼撈取這個dict裡面的單一值**，例如想要撈取第21筆的'BJ'，現在的p1大致上長這樣

{'weight': 2,
 'bet': 1,
 'card_big': 0,
 'card_small': 2,
 'card_total': 2,
 'card_ACE': 0,
 'card_point': 10,
 'ACE_Point': 0,
 'BJ': 'N',
 'Bust': 'N',
 'double_available': 'Y',
 'Stand': 'N',
 'Split_available': 'N',
 'Split_count': 0,
 'Split_ACE': 'N',
 'surrender': 'N'}

## 2.
 **也想要知道怎麼可以篩出全部的'BJ'或是統計'BJ'有幾種結果，這個在後面計算結果也需要用到。**
## 3.
 **請幫忙檢查已完成的地方是否有符合正確使用dataframe的方式，或有沒有效能有問題的地方。**
## 4.  
接下來要寫打法表了，打法表總共會有六種Output跟往下的分支，
  ![Collage Maker-06-Oct-2022-09 02-AM](https://user-images.githubusercontent.com/19257014/194746188-6a816e3a-0411-4026-a3b0-e6557a29c68c.jpg)
  1.Double if possible,otherwise hit     可以就加倍(bet*2)，不可以就補牌(可以的條件是一般拆的牌，或是還沒有要過牌)
  
  2.Double if possible,otherwise stand   可以就加倍(bet*2)，不可以就不動等莊家玩完算結果(可以的條件是一般拆的牌，或是還沒有要過牌)
  
  3.Hit                                  單純要一張牌
  
  4.Split                                拆牌，拆完牌後有分支，看是A拆還是一般拆，A拆就只能各補一張牌後結束，一般拆可以再多拆一輪，也可以選擇Double或hit,stand,surrender，簡單來說就是一般拆可以重進一次打法表判斷(只是要帶入split次數計算上限)
  
  5.Stand                                等莊家結束計算結果。
  
  6.Surrender                            可以就認輸(拿回一半的bet)，可以不用等莊家就寫完這把牌局結果。(可以的條件是一般拆的牌，或是還沒有要過牌)

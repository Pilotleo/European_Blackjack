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
 
 -->要另外寫function計算，例如
 
 def count_BJ(p1_sts):
    if(p1_sts['BJ'] == 'Y'):
        return 1
    else:
        return 0
    
simulation['BJ_times'] =  simulation['p1_sts'].apply(lambda row:count_BJ(row))
simulation['BJ_times'] +=  simulation['p2_sts'].apply(lambda row:count_BJ(row))
simulation['BJ_times'] +=  simulation['p3_sts'].apply(lambda row:count_BJ(row))

print(simulation['BJ_times'].sum())
 
## 3.
 **請幫忙檢查已完成的地方是否有符合正確使用dataframe的方式，或有沒有效能有問題的地方。**
## 4.
**** 新增問題 ****
function split裡面

## 5.
接下來要寫打法表了，打法表總共會有六種Output跟往下的分支，
  ![Collage Maker-06-Oct-2022-09 02-AM](https://user-images.githubusercontent.com/19257014/194746188-6a816e3a-0411-4026-a3b0-e6557a29c68c.jpg)
  1.Double if possible,otherwise hit     可以就加倍(bet*2)，不可以就補牌(可以的條件是一般拆的牌，或是還沒有要過牌)
  
  2.Double if possible,otherwise stand   可以就加倍(bet*2)，不可以就不動等莊家玩完算結果(可以的條件是一般拆的牌，或是還沒有要過牌)
  
  3.Hit                                  單純要一張牌
  
  4.Split                                拆牌，拆完牌後有分支，看是A拆還是一般拆，A拆就只能各補一張牌後結束，一般拆可以再多拆一輪，也可以選擇Double或hit,stand,surrender，簡單來說就是一般拆可以重進一次打法表判斷(只是要帶入split次數計算上限)
  
  5.Stand                                等莊家結束計算結果。
  
  6.Surrender                            可以就認輸(拿回一半的bet)，可以不用等莊家就寫完這把牌局結果。(可以的條件是一般拆的牌，或是還沒有要過牌)
  
## 5.
在判斷式if裡面的lambda還是會執行完整個Dataframe嗎？還是只會執行符合我條件的？例如以下這樣

if p_sts['Split_available'] == 'Y' and p_sts['card_ACE']>0: #AA對拆完補牌後就結束

        simulation['p1_1']=simulation['p1'].apply(lambda row:row[0])
        
        del pop_card('p1',1)
        
        simulation['p1_1']=simulation['card_slot'].apply(lambda row:row[0])
        
        simulation['p1']=simulation['card_slot'].apply(lambda row:row[1])
        
        del pop_card('card_slot',2)
        
        simulation['p1_1_sts']=simulation['p1_1'].apply(lambda row:bf_sts_cal([row][0],bet))
        
        simulation['p1_sts']=simulation['p1'].apply(lambda row:bf_sts_cal([row][0],bet))


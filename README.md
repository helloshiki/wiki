# globalvars 全局表
类型 | 字段 | 说明 
------------ | ------------- | -------------
uint64_t | id | 主键
uint64_t | val | 值

取值：

id | 值 | 说明 
------------ | ------------- | -------------
const uint64_t BETID_ID = 1; | 1 | globalvars 最新的bet_id，递增
const uint64_t TOTAL_BET_AMT_ID = 2; | 2 | globalvars 总下注数量
const uint64_t TOTAL_WON_AMT_ID = 3; | 3 | globalvars 玩家总胜数量
const uint64_t PENDING_AMT_ID = 4; | 4 | globalvars 未开奖的下注数量
const uint64_t INIT_AMT_ID = 5; | 5 | globalvars 系统初始化金额数量
const uint64_t TOTAL_BONUS_ID = 6; | 6 | globalvars 总共发出的BONUS数量
const uint64_t TOTAL_LOST_AMT_ID = 7; | 7 | globalvars 玩家总损失数量
const uint64_t GAME_START_TIMESTAMP_ID = 8; | 8 | globalvars 上线时间 
const uint64_t BONUS_TIMESTAMP_ID = 9; | 9 | globalvars 最新一次分红时间 
const uint64_t AUCTION_BET_S1_ID = 10; | 10 | globalvars 明拍s1
const uint64_t AUCTION_BET_S2_ID = 11; | 11 | globalvars 明拍s2
const uint64_t AUCTION_BET_HS1_ID = 12; | 12 | globalvars 暗拍hs1
const uint64_t AUCTION_BET_HS2_ID = 13; | 13 | globalvars 暗拍hs2
const uint64_t BONUS_AMT_ID = 30; | 30 | globalvars 可分红数量 
const uint64_t TOTAL_LOCKED_KEYS_ID = 31; | 31 | globalvars 总锁定KEYS
const uint64_t DEBUG_MODE_ID = 32; | 32 | globalvars 是否开启调试日志 

# auctions 拍卖状态表
类型 | 字段 | 说明 
------------ | ------------- | -------------
uint64_t | id | 主键
uint64_t | round | 拍卖局数
uint64_t | open | 开局时间
uint64_t | lasttime | 最新叫价时间
uint64_t | keys | 最新叫价
name | user | 叫价用户
uint64_t | eos | 本轮奖励的EOS

说明：
 * id = 1, 表示最新局明拍的状态，可用字段: round, open, lasttime, keys, user, eos
 * id = 2, 表示最新局暗拍的状态，可用字段: round, open, eos

# bidstats 明拍状态表
类型 | 字段 | 说明 
------------ | ------------- | -------------
name | user | 用户, 主键
uint64_t | round | 局数
uint64_t | total | 叫价总KEYS
uint64_t | count | 叫价次数

# bid2history 暗拍状态表
类型 | 字段 | 说明 
------------ | ------------- | -------------
uint64_t | id | 用户, 主键
uint64_t | round | 局数
uint64_t | timestamp | 叫价总KEYS
name | user | 叫价次数
uint64_t | keys | 叫价次数
uint64_t | res1 | 叫价次数

前端用到的字段为: timestamp

# userinfos 用户信息表
类型 | 字段 | 说明 
------------ | ------------- | -------------
name | user | 用户, 主键
uint64_t | available | 可用KEY
uint64_t | lock | 锁定KEY
uint64_t | freeze | 解锁中KEY

# betlogs 下注表
类型 | 字段 | 说明 
------------ | ------------- | -------------
uint64_t | id | 自增主键
name | user | 玩家
name | referral | 推荐人
asset | bet_amt | 下注大小
uint64_t | roll_under | 多少以下为胜，不包括此数字
string | seed | 用户自定义seed
uint64_t | bet_time | 下注时间
checksum256 | tx_hash | 下注对应的EOS交易hash
asset | payout | 用户胜时，可获取的数额


# freezes 解锁表
类型 | 字段 | 说明 
------------ | ------------- | -------------
uint64_t | id | 自增主键
uint64_t | timestamp | 记录产生时间
name | user | 用户
uint64_t | freeze | 解锁数量

# randkeys 解锁表
类型 | 字段 | 说明 
------------ | ------------- | -------------
uint64_t | id | 主键
public_key | key | pubkey

# blacks 黑名单
类型 | 字段 | 说明 
------------ | ------------- | -------------
name | user | 用户, 主键
uint64_t | timestamp | 加入时间

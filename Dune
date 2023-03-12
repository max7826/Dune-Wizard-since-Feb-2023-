select
  date_trunc('day', "block_time") as day, -- get day from block time
  round(sum(value / 1e18), 2) as ETH,  -- Total Deposit ETH Value
  count(distinct "from") as users -- Total Unique Deposit Users
from
  ethereum."transactions"
where
  "to" = '\xFF1F2B4ADb9dF6FC8eAFecDcbF96A2B351680455' -- zk.money Aztec V2
  and substring(data,1,4) = '\x7ff48afb' -- depositPendingFunds function
  and value > 0 -- ONLY ETH deposit is counted, DAI/WBTC are excluded 
  and success
group by
  day

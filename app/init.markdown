# 重要类的初始化
## BatteryStatsHelper
```
//BatteryStatsHelper mStatsHelper =  new BatteryStatsHelper(activity, true);
BatteryStatsHelper mStatsHelper =  new BatteryStatsHelper(this);
```

## PowerProfile
```
PowerProfile powerProfile = mStatsHelper.getPowerProfile();
```

## BatteryStats
```
BatteryStats stats = mStatsHelper.getStats();
```

## BatterySipper
```
final List<BatterySipper> usageList = getCoalescedUsageList(USE_FAKE_DATA ? getFakeStats() : mStatsHelper.getUsageList());
final int numSippers = usageList.size();
for (int i = 0; i < numSippers; i++)
{
    final BatterySipper sipper = usageList.get(i);
}
```

```
BatterySipper sipper = new BatterySipper(DrainType.APP,new FakeUid(UserHandle.getSharedAppGid(Process.FIRST_APPLICATION_UID)), 10.0f);
sipper.packageWithHighestDrain = "dex2oat";
```


## UserHandle 
```
UserHandle userHandle = new UserHandle(UserHandle.getUserId(sipper.getUid()));
```



# Android学习笔记七
-
## ViewPager的使用
### 所需的组件
1. Fragment 以及对应的布局文件
2. Activity 以及布局为viewPager的xml文件

### ViewPager需要Adapter

```
//省略import
public PagerActivity extends FragmentActivity {
	private ViewPager mViewPager;
	private List<Crime> mList;
 	public void onCreate(Bundle saveInstanceState) {
		super.onCreate(saveInstanceState);
		setContentView(R.layout.activity_crime_pager);
		
		mViewPager = (ViewPager) findById(R.id.pager);
		
		FragmentManager fragmentManager = getSupportFragmentManager();
		mViewPager.setAdapter(new FragmentStatePagerAdapter(fragmentManager) {
		@Override
		public Fragment getItem(int position) {
			Crime crime = mCrimes.get(position);
		}
		
		@Override
		public int getCount() {
		return mList.size();
		}
		}) 
	}
}
```



# Android学习笔记八
-
## Fragment之间参数的传递
1. 通过绑定Bundle的fragment传递
2. 处理同一Activity托管的两个fragment之间的数据返回时，可借用Fragment.onActivityResult()方法

### FragmentA:
```
public class FragmentA extends Fragment {
	private static final String ARG_TAG = "tag";
	private DatePicker mDatePicker;
	
	//在FragmentB中调用 返回带有参数的Fragment1
	public static FragmentA newInstance(String argument) {
		Bundle args = new Bundle();
		args.setSerializable(ARG_TAG, argument);
		
		FragmentA fragment = new FragmentA();
		fragment.setArguments(args);
		
		return fragment;
	}
	
	public void onCreateView(~) {
		......
		String argument = (String) getArguments()
							.getSerializable(ARG_TAG);
		new AlertDialog.Builder(getActivity())
                .setView(view)
                .setTitle(R.string.date_picker_title)
                .setPositiveButton(android.R.string.ok, new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int which) {
                        int  year = mDatePicker.getYear();
                        int month = mDatePicker.getMonth();
                        int day = mDatePicker.getDayOfMonth();
                        Date date = new GregorianCalendar(year, month, day).getTime();
                        setResult(Activity.RESULT_OK, date);
                    }
                })
                .create();				
	}
	private void setResult(int resultCode, Date date) {
		if (getTargetFragment == null) {
			return;
		}
		
		Intent intent = new Intent;
		intent.putExtra(EXTRA_DATE, date);
		
		getTargetFragment
		.onActivityResult(getTagetFragmentRequestCode(), resultCode, intent);
}
}
```
### FragmentB:
```
private static final int REQUEST_CODE = -1;

public void onCreateView(~) {
	......
	String argument = "lll";
	mButton.setOnClickListener(new View.OnClickListener() {
		@override
		public void onClick() {
			FragmentA fragment = Fragment1.newInstance(argument);
			fragment.setTagetFragment(FragmentB.this, REQUEST_CODE);
			fragment.show();
		}
	})
}

@override
p


```
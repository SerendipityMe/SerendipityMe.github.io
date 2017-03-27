### 1.在activity_main.xml 文件中添加ExpandableListView。
### 2.MainActivity.java中:
```在oncreate方法中：
expande = (ExpandableListView) findViewById(R.id.expandable);
expande.setAdapter(new expandableAdapter());
```
以下代码可以当内部类或单独文件：
```
class expandableAdapter extends BaseExpandableListAdapter{
  private String[] group ={"groupA","groupB","groupC"};
  private String[][] children = {{"aaa","bbb","ccc"}},{"ddd","eee","fff"},{"ggg","hhh","iii"}};
  public int getGroupCount() {
      return group.length;
  }
  public int getChildrenCount(int groupPosition) {
      return children[groupPosition].length;
  }
  public Object getGroup(int groupPosition) {
      return group[groupPosition];
  }
  public Object getChild(int groupPosition, int childPosition) {
      return children[groupPosition][childPosition];
  }
  public long getGroupId(int groupPosition) {
      return groupPosition;
  }
  public long getChildId(int groupPosition, int childPosition) {
      return childPosition;
  }
  public boolean hasStableIds() {
      return false;
  }
  public View getGroupView(int groupPosition, boolean isExpanded, View convertView, ViewGroup parent) {
      if(convertView==null){
          convertView = getLayoutInflater().inflate(R.layout.groupitem,null);
      }
      TextView text = (TextView) convertView.findViewById(R.id.text);
      text.setText(group[groupPosition]);
      return convertView;
  }
  public View getChildView(int groupPosition, int childPosition, boolean isLastChild, View convertView, ViewGroup parent) {
      if(convertView==null){
          convertView = getLayoutInflater().inflate(R.layout.childitem,null);
      }
      TextView text = (TextView) convertView.findViewById(R.id.text);
      text.setText(children[groupPosition][childPosition]);
      return convertView;
  }
  public boolean isChildSelectable(int groupPosition, int childPosition) {
      return true;
  }
}
```

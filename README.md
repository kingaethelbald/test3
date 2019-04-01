**

## 实验三 UI组件
截图如下：
第一题：

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019040117544599.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmdhZXRoZWxiYWxk,size_16,color_FFFFFF,t_70)

第二题：


![在这里插入图片描述](https://img-blog.csdnimg.cn/20190401180011498.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmdhZXRoZWxiYWxk,size_16,color_FFFFFF,t_70)

第三题：



![在这里插入图片描述](https://img-blog.csdnimg.cn/20190401180227445.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmdhZXRoZWxiYWxk,size_16,color_FFFFFF,t_70)

第四题：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190401180247937.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmdhZXRoZWxiYWxk,size_16,color_FFFFFF,t_70)


代码如下：
```
package com.example.a26081;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.view.Window;
import android.widget.AdapterView;
import android.widget.ListView;
import android.widget.SimpleAdapter;
import android.widget.Toast;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
public class MainActivity extends AppCompatActivity {
    private String[] names = new String[]{"Lion", "Tiger", "Monkey", "Dog", "Cat", "elephant"};
    private int[] image = new int[]{R.drawable.lion, R.drawable.tiger, R.drawable.monkey, R.drawable.dog, R.drawable.cat, R.drawable.elephant};
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        requestWindowFeature(Window.FEATURE_NO_TITLE);
        setContentView(R.layout.animals);
        final int color1 = 0xFF0000;
        final int color2 = 0xFFFFFFFF;
        List<Map<String, Object>> ListItems = new ArrayList<Map<String, Object>>();
        for (int i = 0; i < names.length; i++) {
            Map<String, Object> listItem = new HashMap<String, Object>();
            listItem.put("header", names[i]);
            listItem.put("images", image[i]);
            ListItems.add(listItem);
        }
        SimpleAdapter simpleAdapter = new SimpleAdapter(this, ListItems, R.layout.simple_items, new String[]{"header", "images"}, new int[]{R.id.header, R.id.images});
        final ListView list = (ListView) findViewById(R.id.mylist);
        list.setAdapter(simpleAdapter);
        list.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                int flag = 0;
                System.out.println(names[position] + position + "被单击");
                switch (flag) {
                    case 0:
                        view.setSelected(true);
                        CharSequence text = names[position];
                        int duration = Toast.LENGTH_SHORT;
                        Toast toast = Toast.makeText(MainActivity.this, text, duration);
                        toast.show();
                        flag = 1;
                        break;
                    case 1:
                        view.setSelected(false);
                        CharSequence text1 = names[position];
                        int duration1 = Toast.LENGTH_SHORT;
                        Toast toast1 = Toast.makeText(MainActivity.this, text1, duration1);
                        toast1.show();
                        flag = 0;
                        break;
                }
            }
        });
        list.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener() {
            public void onItemSelected(AdapterView<?> parent, View view, int position, long id) {
                System.out.println(names[position] + "选中");
            }
            public void onNothingSelected(AdapterView<?> parent) {
            }
        });
    }
}
```

```

import android.app.Activity;
import android.os.Bundle;
import android.app.AlertDialog;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import android.widget.Toast;

public class MainActivity extends Activity {

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        View view2 = View.inflate(MainActivity.this, R.layout.activity_main1, null);
        final EditText username = (EditText) view2.findViewById(R.id.username);
        final EditText password = (EditText) view2.findViewById(R.id.password);
        final Button button = (Button) view2.findViewById(R.id. btn_login);
        final Button button1 = (Button) view2.findViewById(R.id.btn_cancel);
        builder.setTitle("安卓软件").setIcon(R.drawable.header_logo).setView(view2);
        final AlertDialog alertDialog1 = builder.create();
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String uname = username.getText().toString().trim();
                String psd = password.getText().toString().trim();
                int duration1 = Toast.LENGTH_LONG;
                if(uname.equals("chx") && psd.equals("123")){
                    Toast toast=Toast.makeText(MainActivity.this,"登录成功!" , duration1);
                    toast.show();
                }
                Toast toast=Toast.makeText(MainActivity.this,"登录失败!" , duration1);
                toast.show();
                alertDialog1.dismiss();
            }
        });
        alertDialog1.show();

    }
}


```
```

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.widget.Toast;
import android.widget.TextView;
import android.graphics.Color;

public class MainActivity extends AppCompatActivity {
    private TextView txt;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    public boolean onCreateOptionsMenu(Menu menu)
    {
        MenuInflater inflater = new MenuInflater(this);
        inflater.inflate(R.menu.menu,menu);
        super.onCreateOptionsMenu(menu);
        return true;
    }
    public boolean onOptionsItemSelected(MenuItem mi){
        txt = (TextView)findViewById(R.id.txt);
        switch (mi.getItemId()){
            case R.id.font_10:
                txt.setTextSize(20);
                break;
            case R.id.font_16:
                txt.setTextSize(32);
                break;
            case R.id.font_20:
                txt.setTextSize(40);
                break;
            case R.id.red_font:
                txt.setTextColor(Color.RED);
                break;
            case R.id.black_font:
                txt.setTextColor(Color.BLACK);
                break;
            case R.id.plain_item:
                Toast toast =Toast.makeText(MainActivity.this,"这是普通单击项",Toast.LENGTH_SHORT);
                toast.show();
                break;
        }
        return true;
    }
}
```
```
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.*;
import android.widget.AbsListView;
import android.widget.ListView;
import android.widget.SimpleAdapter;
import java.util.*;

public class MainActivity extends AppCompatActivity{
    private ListView listView;
    private SimpleAdapter simpleAdapter;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.xml2);
        listView=(ListView)findViewById(R.id.lv);
        simpleAdapter=new SimpleAdapter(this,getData(),R.layout.xml1,new String[]{"pic","text"},new int[]{R.id.iv,R.id.tv});
        listView.setAdapter(simpleAdapter);
        listView.setChoiceMode(ListView.CHOICE_MODE_MULTIPLE_MODAL);
        listView.setMultiChoiceModeListener(new AbsListView.MultiChoiceModeListener() {
            @Override
            public void onItemCheckedStateChanged(ActionMode mode, int position, long id, boolean checked) {
                mode.setTitle(listView.getCheckedItemCount()+" selected");
            }
            @Override
            public boolean onActionItemClicked(ActionMode mode, MenuItem item) {
                // Respond to clicks on the actions in the CAB
                switch (item.getItemId()) {
                    case R.id.i1:
                        mode.finish();
                        return true;
                    default:
                        return false;
                }
            }
            @Override
            public boolean onCreateActionMode(ActionMode mode, Menu menu) {
                MenuInflater inflater = mode.getMenuInflater();
                inflater.inflate(R.menu.menu2, menu);
                return true;
            }
            @Override
            public void onDestroyActionMode(ActionMode mode) {

            }
            @Override
            public boolean onPrepareActionMode(ActionMode mode, Menu menu) {

                return false;
            }
        });
    }
    private List<Map<String,Object>> getData(){
        List<Map<String,Object>> list=new ArrayList<Map<String, Object>>();
        Map<String,Object> map=new HashMap<String, Object>() ;
        map.put("pic",R.mipmap.ic_launcher_round);
        map.put("text","One");
        list.add(map);
        map=new HashMap<String, Object>();
        map.put("pic",R.mipmap.ic_launcher_round);
        map.put("text","Two");
        list.add(map);
        map=new HashMap<String, Object>();
        map.put("pic",R.mipmap.ic_launcher_round);
        map.put("text","Three");
        list.add(map);
        map=new HashMap<String, Object>();
        map.put("pic",R.mipmap.ic_launcher_round);
        map.put("text","Four");
        list.add(map);
        map=new HashMap<String, Object>();
        map.put("pic",R.mipmap.ic_launcher_round);
        map.put("text","Five");
        list.add(map);
        return list;
    }
}

```










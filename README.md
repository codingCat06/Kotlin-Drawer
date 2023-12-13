# Kotlin-Drawer
#  
## 1. Activity_main.xml
### 1) DrawerLayout
#### Drawer에 표시되는 것이 아닌 기본 화면에 표시될 것을 디자인 한다. 또한 첫 레이아웃을 drawerlayout으로 설정한다.
    <androidx.drawerlayout.widget.DrawerLayout
        ... >

        ...

    <androidx.drawerlayout.widget.DrawerLayout>

#  
### 2) NavigationView
#### drawer header / menu 를 지정한다.
    <com.google.android.material.navigation.NavigationView
        android:id="@+id/navigation_view"
        app:menu="@menu/drawer_menu"
        app:headerLayout="@layout/navigation_header"
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        android:fitsSystemWindows="true"/>

#  
#  
## 2. Menu
#### Option Menu 설정하는 것과 같은 방식으로 설정하고 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    tools:showIn="navigation_view">
#### 위와 같은 코드를 추가로 설정한다.
#  
#  

## 3. MainActivity.kt
      lateinit var toggle: ActionBarDrawerToggle
      val drawerlayout = binding.drawerLayout
      val navigation_view = binding.navigationView
      # Layout / View 지정
      
      toggle = ActionBarDrawerToggle(this, drawerlayout, R.string.open, R.string.close )
      # R.string.(open/close) 를 설정 -> drawer open / close event 구문을 다룰 때 사용
      
      drawerlayout.addDrawerListener(toggle)
      toggle.syncState()
      # 초기 상태 동기화

      supportActionBar?.setDisplayHomeAsUpEnabled(true)
      navigation_view.setNavigationItemSelectedListener {
          when(it.itemId){
              R.id.profile -> Toast.makeText(this, "Profile", Toast.LENGTH_SHORT).show()
              R.id.home -> Toast.makeText(this, "Home", Toast.LENGTH_SHORT).show()
              R.id.setting -> Toast.makeText(this, "Setting", Toast.LENGTH_SHORT).show()
          }
          true
      }

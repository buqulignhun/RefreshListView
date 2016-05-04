# RefreshListView
ListView的扩展，你可以根据你的需要添加头部和尾部
 private void listTailUse() {
        listView.setEnabelTail(true);
        listView.setOnDataRefresh(new SubPageRefreshListView.OnDataRefreshListener(){

            @Override
            public void refreshData() {

                    new Thread(){
                        @Override
                        public void run() {
                            SystemClock.sleep(500);
                            System.out.println("---zhixing-");
                            runOnUiThread(new Runnable() {
                                @Override
                                public void run() {
                                    listView.setOnDataRefreshFinished();
                                    Toast.makeText(MainActivity.this, "刷新数据成功", Toast.LENGTH_SHORT).show();
                                }
                            });
                        }
                    }.start();
            }

            @Override
            public void addMoreData() {
               new Thread(){
                   @Override
                   public void run() {
                       SystemClock.sleep(2000);
                       runOnUiThread(new Runnable() {
                           @Override
                           public void run() {
                               listView.setOnDataRefreshFinished();
                               Toast.makeText(MainActivity.this,"加载更多数据成功",Toast.LENGTH_SHORT).show();
                           }
                       });
                   }
               }.start();
            }
        });
    }

    private void listHeaderUse() {
        listView.setEnableHeader(true);
        listView.setOnDataRefresh(new SubPageRefreshListView.OnDataRefreshListener() {
            @Override
            public void refreshData() {
                new Thread(){
                    @Override
                    public void run() {
                        SystemClock.sleep(500);
                        System.out.println("---zhixing-");
                        runOnUiThread(new Runnable() {
                            @Override
                            public void run() {
                                listView.setOnDataRefreshFinished();
                                Toast.makeText(MainActivity.this, "刷新数据成功", Toast.LENGTH_SHORT).show();
                            }
                        });
                    }
                }.start();

            }

            @Override
            public void addMoreData() {

            }
        });
    }

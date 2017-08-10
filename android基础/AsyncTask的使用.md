#### 1、代码注释
```
/**
 * Created by 陈森华 on 2017/8/4.
 * 功能：用一句话描述
 * <p>
 * 泛型参数
 * Params：会传递到doInBackground(Params... params) 方法，需要异步处理的东西，如：传入url，异步加载数据
 * Progress：异步处理进度类型，通过publishProgress（）使onProgressUpdate（）回调，progress作为参数传递
 * Result：处理结果类型，传递至onPostExecute（）和onCancelled（）
 */

class MyTask<Params, Progress, Result> extends AsyncTask<Params, Progress, Result> {
    
    @Override
    protected Result doInBackground(Params... params) {

        return null;
    }

    /**
     * doInBackground执行前回调
     */
    @Override
    protected void onPreExecute() {
        super.onPreExecute();
    }
    /**
     * doInBackground执行完毕后回掉，但取消任务则不会被回调，可以在此处更新UI
     *
     * @param result
     */
    @Override
    protected void onPostExecute(Result result) {
        super.onPostExecute(result);
    }

    /**
     * 调用通过publishProgress（）后会回掉
     *
     * @param values
     */
    @Override
    protected void onProgressUpdate(Progress... values) {
        super.onProgressUpdate(values);
    }

    /**
     * 取消任务会回调
     *
     * @param result
     */
    @Override
    protected void onCancelled(Result result) {
        super.onCancelled(result);
    }

    @Override
    protected void onCancelled() {
    }
```
#### 2、操作

方法 | 意义
---|---
boolean cancle(boolean mayInterruptIfRunning) | 取消任务，参数是否让任务执行完毕。
getStatus() | 返回任务的状态
isCancelled()|判断任务是否再执行完毕前被取消
execute(Params)|执行任务
publishProgress(Progress)|公开进度，使onProgressUpdate（）回掉
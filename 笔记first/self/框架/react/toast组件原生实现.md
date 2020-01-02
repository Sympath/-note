```
function createNotification(params) {
    const div = document.createElement('div');
    const ref = React.createRef();
    document.body.appendChild(div);
    // ref放置在组件上，可以拿到组件的实例
    ReactDOM.render(<Notification ref={ref}/>,div);
    return {
        addNotice(notice){
            return ref.current.addNotice(notice)
        }
    }
}
export default createNotification();
```


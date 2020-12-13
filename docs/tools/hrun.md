

# deleteKey关键字

## hrun版本号
> httprunner版本: 2.0.0

## 作用

> 支持单接口测试：删除某个字段的功能

## 步骤

1. 在httprunner安装包下新建 `ex_requirement.py` , 文件代码如下:

    ``` python

    """
    @File:   ex_requirement.py
    @Time:   2019-2-15 16:29
    @Author: fuqiang523
    @Desc:   扩展需求
    """
    
    # here put the import lib
    
    
    def delete_keys(in_dict):
        if isinstance(in_dict, dict) and 'deleteKey' in in_dict.keys():
            if isinstance(in_dict['deleteKey'], list):
                if str(in_dict['request']['method']).upper() == 'GET':
                    req_url = str(in_dict['request']['url'])
                    url = req_url.split('?')[0] + '?'
                    # request_url.append(new_url)
                    req_param = req_url.split('?')[1].split('&')
                    for item in in_dict['deleteKey']:
                        for key in req_param:
                            key_list = key.split('=')
                            if item in key_list:
                                req_param.remove(key)
                    req_param_str = '&'.join(req_param)
                    in_dict['request']['url'] = url + req_param_str
                else:
                    for item in in_dict['deleteKey']:
                        if 'request' in in_dict.keys():
                            if isinstance(in_dict['request'], dict) \
                                    and 'json' in in_dict['request'].keys() \
                                    and item in in_dict['request']['json']:
                                del in_dict['request']['json'][item]
        return in_dict

    ```

2. 修改 `httprunner\api.py` 代码，如下：

    ``` python
    tests = testcase.get("teststeps", [])
                for index, test_dict in enumerate(tests):
                    for times_index in range(int(test_dict.get("times", 1))):
                        # suppose one testcase should not have more than 9999 steps,
                        # and one step should not run more than 999 times.

    ################################### 新增代码 ##############################
                        from httprunner import ex_requirement
                        test_dict = ex_requirement.delete_keys(test_dict)
    ##########################################################################

                        test_method_name = 'test_{:04}_{:03}'.format(
                            index, times_index)
                        test_method = _add_test(test_runner, test_dict)
                        setattr(TestSequense, test_method_name, test_method)
    ```

3. 使用 `deleteKey` 关键字

    <!-- > ![Image text](images/1.png) -->

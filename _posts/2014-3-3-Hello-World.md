---
layout: post
title: You're up and running!
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below :point_down:).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.

```
class Solution {
public:
    string minRemoveToMakeValid(string s) {
        stack<int> left_parentheses;
        unordered_set<int> to_delete_parentheses;
        int str_size = s.size();
        
        for (int i = 0; i < str_size; i++) {
            if (s[i] == '(') {
                left_parentheses.push(i);
            }
            else if (s[i] == ')') {
                if (left_parentheses.empty()) {
                    to_delete_parentheses.insert(i);
                }
                else {
                    left_parentheses.pop();
                }
            }
        }
        
        while (!left_parentheses.empty()) {
            const auto top_index = left_parentheses.top();
            left_parentheses.pop();
            to_delete_parentheses.insert(top_index);
        }
        
        string res_str = "";
        
        for (int i = 0; i < str_size; i++) {
            if (!to_delete_parentheses.count(i)) {
                res_str += s[i];
            }
        }
        
        return res_str;
        
    }
};
```

---
title: "KMP算法简单实现"
date: 2018-10-04T17:32:30+08:00
draft: true
---

看了B站一个外国小哥讲解的视频，随手撸了一个，只用了一个测试，不保证完全正确，仅供参考。
[B 站视频链接](https://www.bilibili.com/video/av3246487?from=search&seid=12331553402289750602)
```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

void constructNext(const string& pattern, vector<int>& next){
    next.clear();
    next.resize(pattern.size());
    int j = 0;
    int i = 1;
    int count = 0;
    while(i<pattern.size()){
        if(pattern[i]==pattern[j]){
            ++count;
            next[i] = count;
            ++j;
            ++i;
            continue;
        }
        count = 0;
        if(j>0){
            j=next[j-1];
            count=next[j];
            continue;
        }
        ++i;
    }
}

void printNext(const vector<int>& next){
    for(auto& val:next){
        std::cout<<val<<'\t';
    }
    std::cout<<std::endl;
}

int kmpSearch(const string& source, const string& pattern){
    vector<int> next;
    constructNext(pattern,next);
    printNext(next);
    int sourceIt = 0;
    int patternIt = 0;
    while(sourceIt<source.size() && patternIt < pattern.size()){
        if(source[sourceIt] == pattern[patternIt]){
            ++sourceIt;
            ++patternIt;
            continue;
        }
        if(patternIt>0){
            patternIt=next[patternIt-1];
            continue;
        }
        ++sourceIt;
    }
    return patternIt==pattern.size()?(sourceIt-patternIt):0;
}


int main() {
    string source="abxabcabcaby";
    string pattern ="abcaby";
    int match = kmpSearch(source, pattern);
    std::cout<<"the match position is: "<<match << std::endl;
    return 0;
}
```

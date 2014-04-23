---
layout: post
title: "Test New Post(测试新建文章)"
date: 2014-04-23 13:20
categories: test
---

下载: [redis-2.8.8.tar.gz](/res/redis-2.8.8.tar.gz)

![图片测试](/res/选取_015.png)

一些Python代码

{% highlight python %}
class VideoSpider(CrawlSpider):
    name = 'videos'
    start_urls = ['http://unity3d.com/learn/tutorials/modules/beginner']

    def __init__(self):
        self.topics = []
        os.system('mkdir -p /tmp/videos')
        os.system('mkdir videos')
        dispatcher.connect(self.spider_closed, signals.spider_closed)


    def parse(self, response):
        
        sel = Selector(response)
        cur_level_idx = -1
        cur_topic_idx = -1
        cur_topic = None
        cur_topic_path = None
        g12n_lst = sel.css('.g12n')
        
        for g12n in g12n_lst:
            # Header
            if g12n.css('.g12n.mb10'):
                title = g12n.css('.pa20 h1.mb0').xpath('text()').extract()[0]
                descr = g12n.css('.pt10.mb0').xpath('text()').extract()[0]
                cur_topic = {
                    'title': title.strip(),
                    'descr': descr.strip(),
                    'levels': [],
                }
                cur_topic_path = os.path.join('videos', save_filename(cur_topic['title'])).replace(' ', '_')
                cur_level_idx = -1
                cur_topic_idx += 1
                self.topics.append(cur_topic)
            # Section blocks                
            elif g12n.css('.g12n.mb20'): 
                title = g12n.css('.g12 h4').xpath('text()').extract()[0]
                cur_level = {
                    'title': title.strip(),
                    'videos': [],
                }
                cur_path = os.path.join(cur_topic_path, cur_level['title']).replace(' ', '_')
                cmd = 'mkdir -p %s' % cur_path
                self.log('Level.CMD: %s' % cmd)
                os.system(cmd)
                cur_level_idx += 1
                cur_topic['levels'].append(cur_level)
                # One section
                for number, item in enumerate(g12n.css('.g4.mb0 p.mb0 a'), 1):
                    url = item.xpath('@href').extract()[0]
                    url = 'http://unity3d.com/%s' % url
                    title = item.xpath('text()').extract()[0]
                    video = {
                        'number': number,
                        'url': url,
                        'title': title.strip(),
                    }
                    cur_level['videos'].append(video)
                    yield Request(url, callback=self.parse_video,
                                  meta={'cur_path': cur_path,
                                        'cur_topic_idx': cur_topic_idx,
                                        'cur_level_idx': cur_level_idx,
                                        'cur_video_idx': number-1})
            else:
                print 'End Section.'

{% endhighlight %}



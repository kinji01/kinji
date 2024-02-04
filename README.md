<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>{$seo_title}</title>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/app.css' type='text/css' media='all'/>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/default.css' type='text/css' media='all'/>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/pure-highlight.css' type='text/css' media='all'/>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/external.css' type='text/css' media='all'/>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/sweetalert2.min.css' type='text/css' media='all'/>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/diy.css' type='text/css' media='all'/>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/jquery.fancybox.min.css' type='text/css' media='all'/>
<script type='text/javascript' src='{STATIC_URL}meishiu/js/jquery-2.2.4.min.js'></script>
<script type='text/javascript' src='{STATIC_URL}meishiu/js/sweetalert2.min.js'></script>
<link rel='stylesheet' href='{STATIC_URL}meishiu/css/global-styles-inline1.css' type='text/css' media='all'/>
<link href="{SITE_URL}favicon.ico" rel="icon">
<link rel="stylesheet" type="text/css" href="{STATIC_URL}plugin/swiper/css/swiper.min.css" />
<script type="text/javascript" src="{STATIC_URL}plugin/swiper/js/swiper.min.js"></script>
<script type="text/javascript" src="{STATIC_URL}meishiu/js/jquery-1.9.1.min.js"></script>
<meta name="keywords" content="{$keywords}">
<meta name="description" content="{$description}">
<style type="text/css">
@media (min-width: 1200px) { .container,.container-lg,.container-md,.container-sm,.container-xl { max-width:1300px } }
.footer-links {
    text-align: center;
}
</style>

<!-- HTML5 shim, for IE6-8 support of HTML5 elements. All other JS at the end of file. -->
    <!--[if lt IE 9]>
      <script src="{STATIC_URL}meishiu/js/html5shiv.js"></script>
      <script src="{STATIC_URL}meishiu/js/respond.min.js"></script>
    <![endif]-->
    <script>
	if(("standalone" in window.navigator) && window.navigator.standalone){
		var noddy, remotes = false;
		document.addEventListener('click', function(event) {
			noddy = event.target;
			while(noddy.nodeName !== "A" && noddy.nodeName !== "HTML") {
				noddy = noddy.parentNode;
			}
			if('href' in noddy && noddy.href.indexOf('http') !== -1 && (noddy.href.indexOf(document.location.host) !== -1 || remotes)){
				event.preventDefault();
				document.location.href = noddy.href;
			}
	
		},false);
	}
	</script>
</head>
<body class="archive category category-6  max_width hfeed navbar-sticky navbar-slide sidebar-none pagination-infinite_button">
{m:include "index","header"} 
<div class="header-gap"></div>
	<div class="term-bar lazyload visible" data-bg="{$catimg}">
		<a href="{get_category($catid,'pclink')}"><h1 class="term-title">{get_catname($catid)}</h1></a>
		<!-- <h3 class="term-titlea">{$description}</h3> -->
	</div>
<div class="site-content">
	<div class="container">
	<!--   -->
		<div class="filter--content">
				<div class="form-box search-properties mb-0">
					<div class="filter-item">
						<ul class="filter-tag">
							<li><a href="{$site[site_url]}Quanzi" class="on">全部话题</a></li>
                            {php $data = get_childcat($catid);}
        			        {loop $data $k=>$v}
							<li><a href="{$v[pclink]}" {if isset($catid) && $v['catid']==$catid} class="on" {/if} class="">{$v[catname]} </a></li>
							{/loop}
						</ul>
					</div>
				</div>
		</div>
	<!--  -->
			<div class="row">
				<div class="content-column col-lg-9">
					<div class="content-area">
						<main class="site-main">
<!-- 轮播图 开始 -->
		   <div class="row posts-wrapper">
         <div class="col-lg-12">
		  <article class="post post-list">
			<div class="swiper-container yzm-banner">
				 <div class="swiper-wrapper">
		             {m:banner field="title,image,url,typeid,status,introduce" typeid="1" order="id ASC" limit="4"}
		             {loop $data $v}
				      <div class="swiper-slide">
				      	<a href="{$v[url]}">
				      	 <img src="{$v[image]}" alt="{$v[title]}" title="{$v[title]}" />
                         <p class="title">{$v[title]}</p>
				      	</a>
				      </div>
		             {/loop}	
				 </div>
			   </div>
				 <div class="swiper-pagination"></div>
                          </article>
                        </div>
					</div>
<!-- 轮播图 结束 -->
						<div class="row posts-wrapper">
      {m:lists field="id,catid,title,description,url,content,flag,color,thumb,click,inputtime,username,userid,nickname,updatetime,readpoint,up" catid="$catid" limit="10" page="page"}
      {loop $data $v}
          <div class="col-lg-12">
		  <article class="post post-list post-10380 type-post status-publish format-standard has-post-thumbnail hentry category-24 category-jiaocheng tag-52 tag-54 tag-55">
              <div class="entry-wrapper">
                <header class="entry-header">
				<div class="widget widget-userinfo">
					<div class="author-card_content">
						<div class="author_avatar">
							<div class="col-auto">
								<a target="_blank" href="{U('member/myhome/init', array('userid'=>$v['userid']))}" title="{$username}"><img alt='{$v[username]}' title='{$v[username]}' data-src="{get_memberavatar($v['userid'])}" class='lazyload avatar avatar-96 photo qq' height='96' width='96'/></a>
							</div>
							<div class="col n2">
								<a title="{$v[username]}">{$v[username]}</a>
								<small class="d-block"><span class="tips"> {format_time($v['inputtime'],1)}</span></small>
							</div>
							<div class="col-auto">
							<div class="btn btn-qiandao">
								<a href="{get_category($v['catid'], 'pclink')}" style="color:#959595;" title="{get_catname($v['catid'])}"> # {get_catname($v['catid'])}</a>
							</div></div>
						</div>
					</div>
				</div>
					<div class="meta-date">
                  <h2 class="entry-title">
				  {if strstr($v['flag'],'4')}
					<img class="lazyload" src="{STATIC_URL}meishiu/images/zhuti_tuijian.png" style="height: 25px;display: initial;" title="推荐主题">
					{elseif strstr($v['flag'],'5')}
					<img class="lazyload" src="{STATIC_URL}meishiu/images/zhuti_redian.png" style="height: 20px;display: initial;" title="热门主题">
					{elseif $v[readpoint]}
					<img class="lazyload" src="{STATIC_URL}meishiu/images/zhuti_fufei.png" style="height: 20px;display: initial;" title="付费主题">
					{else}
					<img class="lazyload" src="{STATIC_URL}meishiu/images/zhuti_putong.png" style="height: 20px;display: initial;" title="普通主题">
				    {/if}
                    <a href="{$v[url]}" title="{$v[title]}" rel="bookmark">
					{title_color($v['title'], $v['color'])}
					</a>
                  </h2>
					</div>
                </header>
<!--  -->
								<div class="entry-excerpt">
								<a href="{$v[url]}" title="{$v[title]}" rel="bookmark">
								{str_cut($v['description'], 260)}
								</a>
								</div>
							 {if count(getImgs($v['content'])) == 0}
							 {elseif count(getImgs($v['content'])) == 1}
							 {php $data_top = getImgs($v['content'],1);}
							<div class="entrya-media_one">
								<div class="placeholdera">
									{loop $data_top $vv}
									<a href="{$v[url]}">
									<img class="lazyload" data-src="{$vv}" src="{STATIC_URL}meishiu/images/thumb-ing.gif" alt="{$v[title]}" title="{$v[title]}">
									</a>
									{/loop}
								</div>
							</div>
							 {elseif count(getImgs($v['content'])) == 2}
							 {php $data_top = getImgs($v['content'],2);}
							<div class="entrya-media_two">
								<div class="placeholdera">
									{loop $data_top $vv}
									<a href="{$v[url]}">
									<img class="lazyload" data-src="{$vv}" src="{STATIC_URL}meishiu/images/thumb-ing.gif" alt="{$v[title]}" title="{$v[title]}">
									</a>
									{/loop}
								</div>
							</div>
							 {elseif count(getImgs($v['content'])) == 3}
							 {php $data_top = getImgs($v['content'],3);}
							<div class="entrya-media_three">
								<div class="placeholdera">
									{loop $data_top $vv}
									<a href="{$v[url]}">
									<img class="lazyload" data-src="{$vv}" src="{STATIC_URL}meishiu/images/thumb-ing.gif" alt="{$v[title]}" title="{$v[title]}">
									</a>
									{/loop}
								</div>
							</div>
							{elseif count(getImgs($v['content'])) > 4}
							{php $data_bottom = getImgs($v['content'],5);}
							<div class="entrya-media_five">
								<div class="placeholdera">
									{loop $data_bottom $vv}
									<a href="{$v[url]}">
									<img class="lazyload" data-src="{$vv}" src="{STATIC_URL}meishiu/images/thumb-ing.gif" alt="{$v[title]}" title="{$v[title]}">
									</a>
									{/loop}
								</div>
							</div>
								{/if}
<!--  -->
								<div class="entry-footer">
									<ul class="post-meta-boxa">
										<li class="meta-date"><span><i class="fa fa-clock-o"></i> {date('Y-m-d', $v['inputtime'])}</span></li>
										<li class="meta-views"><span title="围观"><i class="fa fa-eye"></i> {$v[click]}</span></li>
										<li class="meta-comment"><span title="回复"><i class="fa fa-comments-o"></i> {get_comment_total($v['id'], $v['catid'], 4)}</span></li>
										<li class="meta-views"><span title="喜欢"><i class="fujian icon-xihuan"></i> {$v[up]}</span></li>
										<!-- <li class="meta-views"><span><i class="fujian icon-002cai-1"></i> {$v[down]}</span></li> -->
									</ul>
								</div>
                              </div>
                         </article>
                       </div>
		            {/loop}
				   </div>
                  <!-- faye -->
					<div class="infinite-scroll-status">
						<div class="infinite-scroll-request">
						</div>
					</div>
					<div class="infinite-scroll-action">
						<div id="page">{$pages}</div>
					</div>
                 <!-- faye -->
</main>
    </div>    </div>
    <div class="sidebar-column col-lg-3">
				<aside class="widget-area">
<!-- 登陆 -->
                      {if intval(get_cookie('_userid'))==0}
                        <div class="widget widget-userinfo">
                            <div class="author-card_content">
                                <div class="author_avatar">
                                    <div class="col-auto">
                                        <img alt="{STATIC_URL}images/default.gif" data-src="{STATIC_URL}images/default.gif" class='lazyload avatar avatar-96 photo qq' height='96' width='96' title='游客' />
                                    </div>
                                    <div class="col n2">游客
                                        <small class="d-block"><span class="tips">您好</span> </small>
                                    </div>
                                </div>
                                <div class="article-qianming">
                                    <a href="{url_referer(1)}"> 登录 </a> | <a href="{U('member/index/register')}"> 立即注册 </a></h4>
                                </div>
                                <!--  -->
                            </div>
                        </div>
                        <!--  -->
					  {else}
                        <div class="widget widget-userinfo">
                            <div class="author-card_content">
                                <div class="author_avatar">
                                    {php $current_userid = intval(get_cookie('_userid'));$userinfo = get_memberinfo($current_userid, true);}
                                    <div class="col-auto">
                                        <a target="_blank" href="{U('member/index/init')}"><img alt="{get_memberavatar(get_cookie('_userid'))}" data-src="{get_memberavatar(get_cookie('_userid'))}" class='lazyload avatar avatar-96 photo qq' height='96' width='96' title='{$userinfo[username]}' /></a>
                                    </div>
                                    <div class="col n2">
                                        <a target="_blank" href="{U('member/index/init')}" title='{$userinfo[username]}'> {$userinfo[username]}</a>
                                        <small class="d-block"><span class="tips">{get_groupname($userinfo['groupid'])}</span> </small>
                                    </div>
                                    <div class="col-auto">
                                        <span class="btn btn-sm btn-white"><a href="{U('member/index/init')}">会员中心</a></span>
                                        <span class="btn btn-sm btn-white"><a href="{U('member/member_content/favorite')}" target="_blank">我的收藏</a></span>
                                    </div>
                                </div>
                                <div class="author-fields">
                                    <div class="row">
                                        <div class="col-4 text-center">
                                            <span class="num">{$userinfo[fans]}</span>
                                            <span class="d-block"><i class="fa fa-skyatlas"></i> 粉丝</span>
                                        </div>
                                        <div class="col-4 text-center">
                                            <span class="num">{$userinfo[experience]}</span>
                                            <span class="d-block"><i class="fa fa-skyatlas"></i> 经验</span>
                                        </div>
                                        <div class="col-4 text-center">
                                            <span class="num">{$userinfo[point]}</span>
                                            <span class="d-block"><i class="fa fa-skyatlas"></i> 积分</span>
                                        </div>
                                    </div>
                                </div>
								{if $userinfo[motto]}
                                <div class="article-qianming">
                                    {$userinfo[motto]}
                                </div>
								{else}{/if}
                                <!--  -->
                            </div>
<!-- 签到 -->
					<div class="pay--content">
						   <div class="pay-box">
							<a href="{$site[site_url]}member/member_circle/init.html?catid=55" class="btn btn--secondary btn--block1 mt-10" style="color: #FFF;font-size: 15px;"><i class="fa fa-send"></i> 发表话题</a>
							{php $get_sign_info = get_sign_info(get_cookie('_userid')); $is_sign = $get_sign_info['status']}
					      {if $is_sign}
							<span class="btn btn--danger btn--block1 mt-10" style="color: #FFF;font-size: 15px;"><i class="fa fa-calendar-check-o"></i> 签到：{if isset($get_sign_info['data'])}{$get_sign_info['data']}{else}0{/if}<sup>天</sup>
							</span>
					{else}
							<a href="javascript:;" onclick="yzm_sign('{U('member/member_sign/init')}')" class="btn btn--danger btn--block1 mt-10" style="color: #FFF;font-size: 15px;" id="yzm_sign"><i class="fa fa-calendar-check-o"></i> 每日签到</a>
					{/if}
						</div>
				   </div>
<!-- 签到 -->
                        </div>
					{/if}
<!-- 搜索 -->
				 <div class="widget widget-userinfo">
                    <h5 class="widget-title mb-3"><i class="mdi mdi-magnify"></i> 搜索话题</h5>
		             <form method="get" action="{U('sousuo/index/init')}" class="search-form">
		              <input type="hidden" name="m" value="search" />
		               <input type="hidden" name="modelid" value="0" id="modelid" />
		                <input type="text" class="form-control" placeholder="话题关键词，回车搜索..." autocomplete="off" value="" name="q" required="required" value="0">
                         </form>
<!-- 人生倒计时 -->
     <div class="sidebar-box classListBox">
     <div class="aside aside-count">
         <div class="content">
             <div class="item" id="dayProgress">
                 <div class="title">今日已经过去<span></span>小时</div>
                 <div class="progress">
                     <div class="progress-bar">
                         <div class="progress-inner progress-inner-1"></div>
                     </div>
                     <div class="progress-percentage"></div>
                 </div>
             </div>
             <div class="item" id="weekProgress">
                 <div class="title">本周已经过去<span></span>天</div>
                 <div class="progress">
                     <div class="progress-bar">
                         <div class="progress-inner progress-inner-2"></div>
                     </div>
                     <div class="progress-percentage"></div>
                 </div>
             </div>
             <div class="item" id="monthProgress">
                 <div class="title">本月已经过去<span></span>天</div>
                 <div class="progress">
                     <div class="progress-bar">
                         <div class="progress-inner progress-inner-3"></div>
                     </div>
                     <div class="progress-percentage"></div>
                 </div>
             </div>
             <div class="item" id="yearProgress">
                 <div class="title">今年已经过去<span></span>个月</div>
                 <div class="progress">
                     <div class="progress-bar">
                         <div class="progress-inner progress-inner-4"></div>
                    </div>
                     <div class="progress-percentage"></div>
                 </div>
             </div>
         </div>
     </div>
 </div>
 <!-- 人生倒计时 -->
				   </div>
				<!-- 搜索菜谱 -->
				 <div class="widget widget-userinfo">
                    <h5 class="widget-title mb-3"><i class="mdi mdi-magnify"></i> 搜索菜谱</h5>
		             <form method="get" action="{U('search/index/init')}" class="search-form">
		              <input type="hidden" name="m" value="search" />
		               <input type="hidden" name="modelid" value="0" id="modelid" />
		                <input type="text" class="form-control" placeholder="请输入菜名，回车搜索..." autocomplete="off" value="" name="q" required="required" value="0">
                         </form>
				         {m:tag field="id,tag,total" order="RAND()" limit="21"}
						 <div class="tagcloud">
	                     <a target="_blank" href="{SITE_URL}search/index/init.html?m=search&c=index&a=init&modelid=0&q=家常" alt="家常菜" class="tag-cloud-link" rel="tag" title="家常菜">家常菜</a>
	                     <a target="_blank" href="{SITE_URL}search/index/init.html?m=search&c=index&a=init&modelid=0&q=下饭" alt="下饭菜" class="tag-cloud-link" rel="tag" title="下饭菜">下饭菜</a>
	                     <a target="_blank" href="{SITE_URL}search/index/init.html?m=search&c=index&a=init&modelid=0&q=快手" alt="快手菜" class="tag-cloud-link" rel="tag" title="快手菜">快手菜</a>
	                     <a target="_blank" href="{SITE_URL}search/index/init.html?m=search&c=index&a=init&modelid=0&q=早餐" alt="早餐" class="tag-cloud-link" rel="tag" title="早餐">早餐</a>
	                     <a target="_blank" href="{SITE_URL}search/index/init.html?m=search&c=index&a=init&modelid=0&q=凉菜" alt="凉菜" class="tag-cloud-link" rel="tag" title="凉菜">凉菜</a>
	                     <a target="_blank" href="{SITE_URL}index/index/lists/catid/1/biaoqian/%25E7%25B4%25A0%25E9%25A3%259F/s/1.html" alt="素食" class="tag-cloud-link" rel="tag" title="素食">素食</a>
	                     <a target="_blank" href="{SITE_URL}Caipu/hongbei/" alt="烘焙" class="tag-cloud-link" rel="tag" title="烘焙">烘焙</a>
	                     <a target="_blank" href="{SITE_URL}index/index/lists/catid/1/biaoqian/%25E4%25B8%25BB%25E9%25A3%259F/s/1.html" alt="主食" class="tag-cloud-link" rel="tag" title="主食">主食</a>
	                     <a target="_blank" href="{SITE_URL}Localsnack" alt="小吃" class="tag-cloud-link" rel="tag" title="小吃">小吃</a>
						 {loop $data $v}
	                     <a target="_blank" href="{SITE_URL}tag/{$v['id']}.html" alt="{$v[tag]}" class="tag-cloud-link" rel="tag" title="{$v[tag]}">{$v[tag]} ({$v[total]})</a>
						 {/loop}
                        </div>
				   </div>
				<!-- 搜索菜谱 -->
<!-- 评论 -->
                <div class="widget widget-comments">
                 <h5 class="widget-title"><i class="fa fa-comments-o"></i> 最新评论</h5>
                  <ul>
                   {m:comment_newest limit="5"}
                   {loop $data $v}	
                    <li>
                    <a target="_blank" href="{$v[url]}" title="{$v[title]}">
	                <div class="inner">
                     <img alt="" src="{get_memberavatar($v['userid'])}" srcset="{get_memberavatar($v['userid'])}" class="avatar avatar-96 photo avatar-default" height="96" width="96" loading="lazy"/>
		             <time>
		            <strong>{if $v['userid']}{$v[username]}{else}网友评论{/if}</strong>
		            {format_time($v['inputtime'],1)}《{str_cut($v['title'],32)}》
		            </time>
		           <small>{str_cut($v['content'],168)}</small>
                  </div>
		          </a>
                 </li>
				 {/loop}
                 </ul></ul>
               </div></div>
<!-- 排行 -->
                 <div class="widget widget-userstop"><div class="widget widget-userstop">
                  <h5 类=“小部件标题”><h5 class="widget-title">
				  <a href="#" title="排行榜"><img src="{STATIC_URL}meishiu/images/ranking.png" style="浮动：左浮动：左;"></a> 积分排行<a href="#" title="排行榜"><img src="{STATIC_URL}meishiu/images/ranking.png" style=";"></a>&nbsp;积分排行
				  </h5></h5>
				 
                   <ul>               <ul>
	                {m:get sql="select userid,username,point from yzm_member order by point desc" limit="5"}                {m:get sql="select userid,username,point from yzm_member order by point desc" limit="5"}
	                {循环$数据$v}                {loop $data $v}
                     <li><span class="avatar">
                      <a target="_blank" href="{U('member/myhome/init', array('userid'=>$v['userid']))}" title="{$v[用户名]}" >
		                <img alt='' data-src="{get_memberavatar($v['userid'])}" class='lazyload 头像 avatar-96 照片 qq' height='96' width='96' /></a >	                <img alt='' data-src="{get_memberavatar($v['userid'])}" class='lazyload avatar avatar-96 photo qq' height='96' width='96' /></a>
		                </span>	                </span>
		                <span class="name">{$v[用户名]}</span>	                <span class="name">{$v[username]}</span>
                       <span class="credits"><span class="num">{$v[point]}</span>积分</span> <span class="credits"><span class="num">{$ v[point]}</span>积分</span>
                      </li></li>
		             {/环形} {/环形}
                    </ul>
                   </div>
<!-- 广告 -->
				<div class="widget cao-widget-posts">
						<div class="author_avatar">
							{广告(2)}
						</div>
				</div>
<!-- 广告2
				<div class="widget widget-userinfo">
					<div class="author-card_content">
							<a target="_blank" href="{$site[site_url]}Localsnack" class="name">
							<img class="lazyload" data-src="{STATIC_URL}meishiu/images/quanzi_b.jpg" title="地方小吃"/>
						 </a>
					</div>
				</div>
<!-- -->
      </旁>
    </div>
  </div> </div> _ _  _ _ _
</div> _ _ > _ _

  </div> _ _ _
</div> _ _ _
	<!-- #main -->
<脚本类型=“text/javascript”src =“ <?php echo STATIC_URL;?> plugin/laydate/1.1/laydate.js”> </脚本>
{ m:include "索引","页脚"}

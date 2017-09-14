---
id: 2663
title: 'JRockit GC in Action[转]'
date: 2012-03-01T20:37:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2663
permalink: '/2012/03/01/jrockit-gc-in-action%e8%bd%ac/'
views:
  - "3202"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
---
From: [http://java.dzone.com/articles/jrockit-gc-action](http://java.dzone.com/articles/jrockit-gc-action "http://java.dzone.com/articles/jrockit-gc-action")

&#160;

<div>
  <div>
    <h1>
      <span style="word-spacing: 0px; font: medium tahoma; text-transform: none; color: rgb(0,0,0); text-indent: 0px; white-space: normal; letter-spacing: normal; border-collapse: separate; orphans: 2; widows: 2; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">JRockit GC in Action</span>
    </h1></p>
  </div>
  
  <div>
    <span style="word-spacing: 0px; font: medium tahoma; text-transform: none; color: rgb(0,0,0); text-indent: 0px; white-space: normal; letter-spacing: normal; border-collapse: separate; orphans: 2; widows: 2; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">July 12, 2011 AT 10:29 PM</span>
  </div>
  
  <p>
    <span style="word-spacing: 0px; font: medium tahoma; text-transform: none; color: rgb(0,0,0); text-indent: 0px; white-space: normal; letter-spacing: normal; border-collapse: separate; orphans: 2; widows: 2; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">In this article I would like to elaborate on the garbage collection specifics of Oracle&#8217;s JRockit JVM. Recently JRockit has been made free for use and many people may consider using it instead of another widely popular Oracle JVM &#8211; HotSpot (former Sun&#8217;s JVM). I have more experience with HotSpot JVM, so my opinion may be biased a little, but I will try to stick to the facts as much as I can.</span>
  </p>
  
  <p>
    <span style="word-spacing: 0px; font: medium tahoma; text-transform: none; color: rgb(0,0,0); text-indent: 0px; white-space: normal; letter-spacing: normal; border-collapse: separate; orphans: 2; widows: 2; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"><strong>Disclaimer:</strong><span>&#160;</span><em>This article expresses my personal opinion based on my practical experience with JRockit and HotSpot JVMs. My experience is limited by few use cases. Conclusions from this article may not be valid for other use cases. I&#8217;m not pretending that I have completed comprehensive research of JRockit&#8217;s GC behavior.</em></span>
  </p>
  
  <h3>
    JRockit garbage collection algorithms
  </h3>
  
  <p>
    JRockit uses mark-sweep-compact (MSC) as its base garbage collection algorithm, though it allows a lot of tweaking. The JVM command line option -Xgc: allows to choose variations of MSC algorithm. The following variations are available in JRockit R28:
  </p>
  
  <table>
    <tr>
      <td>
        <p>
          <strong>-Xgc: option</strong>
        </p>
      </td>
      
      <td>
        <p>
          <strong>Generational</strong>
        </p>
      </td>
      
      <td>
        <p>
          <strong>Mark</strong>
        </p>
      </td>
      
      <td>
        <p>
          <strong>Sweep</strong>
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          genconcon or gencon
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          singleconcon or singlecon
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          genconpar
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          singleconpar
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          genparpar or genpar
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          singleparpar or singlepar
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          genparcon
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
    </tr>
    
    <tr>
      <td>
        <p>
          singleparcon
        </p>
      </td>
      
      <td>
        &#160;
      </td>
      
      <td>
        <p>
          parallel
        </p>
      </td>
      
      <td>
        <p>
          concurrent
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    There are also special values for -Xgc: (prior to R28 -XgcPrio: was used for this) options which instruct the JVM to use heuristics to choose best algorithm in run-time (unlike HotSpot JRockit can switch algorithms while the JVM is running, though documentation says that R28 is likely to stick with one algorithm).
  </p>
  
  <ul>
    <li>
      -Xgc:throughput &#8211; best throughput,
    </li>
    <li>
      -Xgc:pausegen &#8211; minimal pauses,
    </li>
    <li>
      -Xgc:deterministic &#8211; minimal pauses, stable pause time.
    </li>
  </ul>
  
  <p>
    I personally found these heuristics quite useless though. In practice, the JVM tends to choose singlecon strategy for low pause target, which IMHO critically lacks throughput for server type applications.
  </p>
  
  <h3>
    Generational vs single space
  </h3>
  
  <p>
    In my<span>&#160;</span><a title="How to tame java GC pauses? Surviving 16 GiB heap and greater" href="http://java.dzone.com/articles/how-tame-java-gc-pauses" target="_blank" shape="rect">previous article<span>&#160;</span></a>, I explained the idea behind generational garbage collection. The generational approach assumes that space is divided into young and old space, each of which are collected by different algorithms (young space employs copy collector, while old space more sophisticated mark-sweep-compact). Keeping young and old space separate, requires the JVM to implement some kind of barrier to track old-to-young references. In generational mode JRockit uses a card marking barrier similar to one in HotSpot&#8217;s CMS and throughput collectors (HotSpot&#8217;s G1 is the only mainstream collector using other type of barrier). Unlike HotSpot which is always using generational approach, JRockit can operate in single space mode. Single space mode means:
  </p>
  
  <ul>
    <li>
      no young collection pauses,
    </li>
    <li>
      no write barrier unless it is needed for old space collector,
    </li>
    <li>
      more frequent old collection pauses,
    </li>
    <li>
      orders of magnitude worse throughput compared to generational collector.
    </li>
  </ul>
  
  <p>
    To be honest, I have never worked with application which could benefit from single space collector. Though I cannot deny the possibility of their existence.
  </p>
  
  <h3>
    Parallel vs concurrent
  </h3>
  
  <p>
    Parallel collectors require stop-the-world pause for the whole duration of major collection phases (mark or sweep), but employ all available cores to compress pause time. Parallel collectors usually have better throughput, but they are not a good fit for pause critical applications. Concurrent collector tries to do most work concurrently (though it also does it in parallel on multi-core systems), stopping the application only for short duration. The concurrent collection algorithm in JRockit is fairly different from both HotSpot&#8217;s concurrent collectors (CMS and G1). I will explain how it works in details later in this article.
  </p>
  
  <h3>
    A Few differences between JRockit and HotSpot
  </h3>
  
  <h3>
    Heap geometry
  </h3>
  
  <p>
    The HotSpot JVM has fixed heap geometry, in particular young, tenured and permanent spaces have fixed address ranges during the JVM life time (though physical memory may be partially committed). On the contrary, JRockit has single heap space. If a generational collection algorithm is used, some part of this space will be used for nursery (young space), though nursery in JRockit is not necessary continuous. The same is true for keep space (equivalent of survivor space in HotSpot). Both nursery and keep space may drift in the heap during JRockit&#8217;s JVM life time. JRockit has no analog of HotSpot&#8217;s permanent space.
  </p>
  
  <h3>
    Aging of objects in young space
  </h3>
  
  <p>
    HotSpot keeps the exact age (in terms of survived collection) associated with each object in young space. Using this knowledge HotSpot can keep an object in young space through several collections, which is an effective way to fight medium-aged garbage without increasing young space (though increasing young space is usually better in terms of performance). JRockit does not keep objects age, so objects are always promoted on second collection (first collection will move object to keep area, and second to old space).
  </p>
  
  <h3>
    Thread local allocation blocks and pauses
  </h3>
  
  <p>
    Both HotSpot and JRockit use TLABs (thread local allocation blocks) for fast object allocation. TLABs are allocated in young space/nursery (in single space mode, JRockit allocates TLABs in old space). Threads allocate new objects in their TLABs, and when a TLAB gets full, the thread requests a new one from the memory manager.
  </p>
  
  <p>
    In HotSpot, all TLABs are recycled during young space collection (which is usually triggered by particular thread requesting TLAB block). JRockit is different, failure to allocate a new TLAB will trigger young GC, but it is not guaranteed that GC will start immediately or that GC will free enough continuous memory for TLAB. In later cases, the thread will be blocked waiting for TLAB while the JVM technically is not in stop-the-world pause. In other words, JRockit has two types of application pauses: stop-the-world pauses and TLAB wait pauses (affecting individual threads). From an application point of view, thread pauses are as bad as stop-the-worlds ones. It is impossible to guarantee service of application if random threads are blocked. The JVM may not fairly report TLAB wait pauses, so it is possible that application will experience pauses not reported by GC logs.
  </p>
  
  <p>
    Concerning TLAB sizes, HotSpot is more aggressive for growing TLABs compared to JRockit. JRockit is more conservative because TLABs may survive several young collections. HotSpot recycles all TLABs in each young collection, so large TLABs are not going to be wasted if the thread would stop actively allocating objects.
  </p>
  
  <h3>
    JRockit&#8217;s concurrent collector
  </h3>
  
  <p>
    JRockit has a very sophisticated concurrent collector. It is a variation of mark-sweep-compact algorithm. During mark phase, collector is traversing object graph marking all reachable objects. During sweep phase, whole heap is scanned and space from non-marked objects is reclaimed. Compact phase relocate objects in heap, fighting with fragmentation. JRockit can execute mark and sweep phases in concurrent mode. Concurrent implementation of mark phase requires breaking it into 3 sub phases:
  </p>
  
  <ul>
    <li>
      initial mark &#8211; stop-the-world pause to collect root references,
    </li>
    <li>
      concurrent marking &#8211; traversing graph without blocking application,
    </li>
    <li>
      remark &#8211; stop-the-world pause needed to account changes made by application during concurrent phase. During remark collector only have to revisit references changed since initial mark (card marking write barrier allow to do it efficently).
    </li>
  </ul>
  
  <p>
    In practice, both JRockit and HotSpot are using additional phase &#8211; concurrent preclean &#8211; which executed before remark. Concurrent preclean is actually a remark but without stop-the-world pause. Preclean phase makes next remark phase shorter by reducing number of cards which have to be rescanned.
  </p>
  
  <p>
    Concurrent marking is fairly straight forward. Sweeping also can be done concurrently with application (JRockit is using two short stop-the-world pause for sweeping, while HotSpot&#8217;s sweep phase is fully concurrent). But if we just mark unused objects as free space it would eventually lead to fragmentation of heap and inability to allocate objects of moderate size, even if free space is available (death by fragmentation). JRockit is using compaction to protect itself against fragmentation.
  </p>
  
  <p>
    Compaction is a very expensive operation. The JVM should move not only the object itself, it should also update all references to every relocated object. Compaction also requires stop-the-world pause and is single threaded in JRockit JVM. To avoid long compaction pauses, the garbage collector can do compaction incrementally. Each time when concurrent collection is stated, the JVM selects a range of heap space to be compacted. During the mark phase all references to objects in compaction area are collected. During the sweep phase, unreachable objects are marked as free space. And finally during the compact phase objects in compaction area are relocated. Compaction can be either internal (objects are relocated inside of compaction region), or external (objects are copied out to another region and whole old region becomes a free space). Compaction phase is abortable, JVM may choose to abort compaction half way if it is taking too much time. JVM may also decide not to move some objects if they have too many external references (or if they are pinned).
  </p>
  
  <p>
    Even done incrementally compaction is significantly increasing pause duration. It is possible to turn off compaction altogether, but this way fragmentation becomes serious treat (unlike HotSpot&#8217;s CMS, JRockit is not using free lists and statistical analysis to control fragmentation of heap).
  </p>
  
  <h3>
    JRockit&#8217;s gencon vs HotSpot&#8217;s CMS quick summary
  </h3>
  
  <p>
    Both use 4 phase concurrent marking (initial mark, concurrent sweep, concurrent preclean, remark). HotSpot&#8217;s CMS is using fully concurrent sweep (without compaction).
  </p>
  
  <p>
    JRockit may use compaction, compaction requires additional pause.
  </p>
  
  <p>
    In JRockit initial mark and remark are forcing young collection. In HotSpot it is more flexible. Initial mark may wait for next young GC, while remark either force it or scan objects in Eden without young GC.
  </p>
  
  <p>
    HotSpot&#8217;s CMS is using free lists and statistical analysis to avoid fatal heap fragmentation. JRockit can do compaction, but very prone to fragmentation if compaction is not frequent enough.
  </p>
  
  <h3>
    Configuring JRockit for low pause on large heap
  </h3>
  
  <p>
    Garbage collection tuning is very application specific. So everything below has been written with certain type of applications in mind. Application class I&#8217;m interested in is same as in previous article. Its key characteristics are:
  </p>
  
  <ul>
    <li>
      Heap is used to store data structures in memory.
    </li>
    <li>
      Heap size 10GiB and more.
    </li>
    <li>
      Request execution time is small (up to dozens of milliseconds).
    </li>
    <li>
      Transactions are short (up to hundreds of milliseconds). Transaction may include several requests.
    </li>
    <li>
      Data in memory is modified slowly (e.i. we do not modify whole 10GiB in heap within one seconds, though updating of 10MiB data in heap per second is ok).
    </li>
    <li>
      Amount of short lived garbage is fairly large ~100-200MiB sec (garbage produced by parsing encoding network protocol, etc).
    </li>
  </ul>
  
  <p>
    Only viable algorithm for such kind of application is generational concurrent mark sweep. Unfortunately heuristic algorithms are not smart enough and will force single space concurrent algorithm for low pause target (they have their metric, they want to avoid young GC pauses). Achilles&#8217; heel of single space algorithm is throughput, which is too low for this class of applications.
  </p>
  
  <p>
    We have to for gencon algorithm and tune it by hands.
  </p>
  
  <h3>
    Sizing young space
  </h3>
  
  <p>
    Default size of young space in JRockit is 10MiB multiplied by number of young collection threads (young collection is done in parallel). Usually this default size is too small and you would want to increase it to reduce young GC frequency (-Xns<size> JVM option will help you). Compared to HotSpot, JRockit young space collection pauses are considerably shorter.
  </p>
  
  <h3>
    Keeping compaction pauses under control
  </h3>
  
  <p>
    JVM can abort compaction if it is taking too long. This is effective way to ensure max pause guaranty. Unfortunately you cannot just say -XpauseTarget=50 and relax. JRockit forbids pause target below 200ms if GC type is not set to deterministic, but if you use -Xgc:deterministic, JVM will choose singlecon mode and you will enjoy 5-30 second pauses (dependent on heap size) due to lack of throughput. This is really sad.
  </p>
  
  <p>
    Due to pause target is locked out from our use, we have to use other options. There are too ways how we can prohibit long compaction:
  </p>
  
  <ul>
    <li>
      limiting size of compaction area (using -XXcompation:percentage=n option),
    </li>
    <li>
      limiting number of references to be updated during compaction (using -XXcomaption: maxReferences=n).
    </li>
  </ul>
  
  <p>
    Both ways are bad. Reducing size of compaction area will limit compaction pause time, but will reduce throughput. Using maxReferences will abort compaction if area is containing too many live objects, avoiding long pauses but reducing throughput even more. Let&#8217;s hope JRockit team will realize demand from application with large heap and unlock access for pause target.
  </p>
  
  <h3>
    Running on 32GiB heap, good, bad and ugly.
  </h3>
  
  <p>
    Now I would like to share my experience of running 32GiB Oracle Coherence node on JRockit. Though I have spent enough time with tuning of GC options, there is still a fair chance that I have missed something. So please take my opinion with a grain of salt.
  </p>
  
  <h3>
    Good, young GC pause times
  </h3>
  
  <p>
    Young GC pause time are much better than HotSpot&#8217;s CMS. It is roughly on par with<span>&#160;</span><a title="OpenJDK patch cutting down GC pause duration up to 8 times" href="http://aragozin.blogspot.com/2011/07/openjdk-patch-cutting-down-gc-pause.html" target="_blank" shape="rect">patched version of JDK7<span>&#160;</span></a>(even slightly better). Young collections are most frequent ones, this is really good that JRockit can handle them so well.
  </p>
  
  <h3>
    Bad, throughput
  </h3>
  
  <p>
    It is just not enough. I believe it is a curse of any compacting collector (HotSpot&#8217;s G1 included). Modern hardware is just not enough to do all work associated with object relocation fast enough. But lack of throughput may not necessary be a show stopper. While my tests are fairly write intensive, for many applications JRockit&#8217;s generational collector throughput may be enough.
  </p>
  
  <p>
    In terms of throughput HotSpot&#8217;s CMS beats out all competitors (probably except Azul Zing, which is using some intimate access to hardware not possible for common JVMs like HotSpot or JRockit).
  </p>
  
  <h3>
    Bad, fragmentation
  </h3>
  
  <p>
    Surprise! Compacting collector is prone to fragmentation. Combination of low throughput and incremental compaction leads to a fragmentation. Increasing throughput probably would remedy this problem, but it is impossible without significant increase in pause duration. Another way to counter fragmentation is increasing heap size, but this approach also have obvious practical limitation.
  </p>
  
  <h3>
    Ugly, long pauses
  </h3>
  
  <p>
    If you are looking only at logs of JRockit&#8217;s GC, you may be kept under the assumption that pauses are short and low throughput is the only issue. It is not true. Your application may experience pauses not reported by JVM. You can easily measure them in your application code, though. After spending some time investigating this problem, I came to conclusion that the concurrent preclean phase is hindering young collection.
  </p>
  
  <p>
    Normally young collection starts immediately, if TLAB cannot be allocated. But if concurrent preclean is active at the same time, it seems that the young collection can be delayed (and this delay can be significant 0.5-2 seconds depending on preclean phase duration). During that time threads are blocked waiting for TLAB. TLABs are usually small enough, so you have a good chance that most worker threads of your application will be blocked waiting for TLAB allocation. This is as severe as normal stop-the-world pause except, JVM does not report anything.
  </p>
  
  <div>
    <img title="Image" style="border-top-width: 0px; display: inline; border-left-width: 0px; border-bottom-width: 0px; cursor: default; border-right-width: 0px" height="248" alt="Image" src="http://www.beansoft.biz/wp-content/uploads/2012/03/Image.png" width="512" border="0" />
  </div>
  
  <p>
    Why is preclean is affecting young collection? It is a good question, one possible reason is that remark which is scheduled after preclean requires young collection anyway, and the JVM thinks that this way it can avoid 2 pauses. Or it may be young collection interferes with concurrent preclean somehow using sharing data structures, so the JVM decides to delay it. The reason is not clear for me, but the consequence is unpredictable long application pauses which cannot be controlled.
  </p>
  
  <p>
    This behavior is a serious show stopper for using JRockit in pause sensitive applications.
  </p>
  
  <h3>
    Deterministic pauses myth
  </h3>
  
  <p>
    JRockit claims what it can guarantee deterministic short pauses (below 50ms). This claim is absolutely valid. Single space concurrent collector, fully controls duration of pauses, so it can provide this guarantee. The problem is extremely low throughput though. Throughput can be increased by throwing in more memory for the application. But it will probably require tens or even hundreds times memory overhead to provide throughput comparable to the generational collector.
  </p>
  
  <h3>
    Conclusion
  </h3>
  
  <p>
    JRockit is a nice product, it has a lot of advanced features and is a very mature JVM. But so far I&#8217;m not going to use it for response time sensitive applications. Still I believe JRockit has good potential. There may also be kinds applications which can benefit from JRockit&#8217;s garbage collection algorithms better than typical data grid.
  </p>
  
  <p>
    Anyway it is good to have fair competition in the JVM area. Good luck to both JRockit and HotSpot products!
  </p>
  
  <h3>
    See also
  </h3>
  
  <p>
    Some of my other articles about garbage collection.
  </p></p>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JRockit GC in Action[转]](http://www.beansoft.biz/2012/03/01/jrockit-gc-in-action%e8%bd%ac/)
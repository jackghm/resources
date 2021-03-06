blog post is https://richardimaoka.github.io/blog/persistent-actor-minimal-sql

## Instruction to run the example
```
> git clone https://github.com/richardimaoka/resources.git
> cd resources
> cd persistent-actor-minimal-sql
> sbt
> runMain example.Main
```

## Output 
```
> runMain example.Main
[info] Running example.Main 
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: Defaulting to no-operation (NOP) logger implementation
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
receiveCommand  : Received Command(1)
[WARN] [SECURITY][01/18/2018 05:39:25.593] [exampleSystem-akka.persistence.dispatchers.default-plugin-dispatcher-6] [akka.serialization.Serialization(akka://exampleSystem)] Using the default Java serializer for class [example.Event] which is not recommended because of performance implications. Use another serializer or disable this warning using the setting 'akka.actor.warn-about-java-serializer-usage'
persist callback: Event = Event(1) persisted
persist callback: current state = 1
receiveCommand  : Received Command(2)
persist callback: Event = Event(2) persisted
persist callback: current state = 3
receiveCommand  : Received Command(3)
persist callback: Event = Event(3) persisted
persist callback: current state = 6
[ERROR] [01/18/2018 05:39:26.919] [exampleSystem-akka.actor.default-dispatcher-5] [akka://exampleSystem/user/p1] exploded!
java.lang.Exception: exploded!
	at example.MyPersistentActor$$anonfun$receiveCommand$1.applyOrElse(Main.scala:37)
	at akka.actor.Actor.aroundReceive(Actor.scala:517)
	at akka.actor.Actor.aroundReceive$(Actor.scala:515)
	at example.MyPersistentActor.akka$persistence$Eventsourced$$super$aroundReceive(Main.scala:11)
	at akka.persistence.Eventsourced$$anon$1.stateReceive(Eventsourced.scala:663)
	at akka.persistence.Eventsourced.aroundReceive(Eventsourced.scala:183)
	at akka.persistence.Eventsourced.aroundReceive$(Eventsourced.scala:182)
	at example.MyPersistentActor.aroundReceive(Main.scala:11)
	at akka.actor.ActorCell.receiveMessage(ActorCell.scala:527)
	at akka.actor.ActorCell.invoke(ActorCell.scala:496)
	at akka.dispatch.Mailbox.processMailbox(Mailbox.scala:257)
	at akka.dispatch.Mailbox.run(Mailbox.scala:224)
	at akka.dispatch.Mailbox.exec(Mailbox.scala:234)
	at akka.dispatch.forkjoin.ForkJoinTask.doExec(ForkJoinTask.java:260)
	at akka.dispatch.forkjoin.ForkJoinPool$WorkQueue.runTask(ForkJoinPool.java:1339)
	at akka.dispatch.forkjoin.ForkJoinPool.runWorker(ForkJoinPool.java:1979)
	at akka.dispatch.forkjoin.ForkJoinWorkerThread.run(ForkJoinWorkerThread.java:107)

receiveRecover  : Recovering an event = Event(1)
receiveRecover  : current state = 1
receiveRecover  : Recovering an event = Event(2)
receiveRecover  : current state = 3
receiveRecover  : Recovering an event = Event(3)
receiveRecover  : current state = 6
receiveCommand  : Received Command(4)
persist callback: Event = Event(4) persisted
persist callback: current state = 10
receiveCommand  : Received Command(5)
persist callback: Event = Event(5) persisted
persist callback: current state = 15
[success] Total time: 20 s, completed Jan 18, 2018 5:39:30 AM
```

## References 

- Official documentation at https://doc.akka.io/docs/akka/2.5.9/persistence.html

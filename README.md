# Subject_Angular
Subject , ReplaySubject, BehaviorSubject &amp; AsyncSubject

import { AsyncSubject, BehaviorSubject, ReplaySubject, Subject } from 'rxjs';

/// (1)subject
const subjectSe = new Subject();

//call this subject
subjectSe.subscribe((d) => console.log(d));
// add data to subject
subjectSe.next('Hrushikesh Das');

// call again
subjectSe.subscribe((d) => console.log(d)); // output is nothing because it is declared one time

//for this type of situation we need to add behaviorsubject

//(2) behaviorsubject

const behaviorsubject = new BehaviorSubject(1); // need to initialize the data

//call this BehaviorSubject
behaviorsubject.subscribe((d) => console.log(d)); // output is 2
// add data to subject
behaviorsubject.next(2);

// call again
behaviorsubject.subscribe((d) => console.log(d)); //. also 2

// (3)one more situation ,

behaviorsubject.next(3);
behaviorsubject.next(4);
behaviorsubject.next(5);
behaviorsubject.subscribe((d) => console.log(d)); //output is 5 , means only getting new or latest updated value . So for this type of situation we are using ReplaySubject

// ReplaySubject.

const replaySubject = new ReplaySubject(2); // 2 is the latest number of value
replaySubject.next(10);
replaySubject.next(11);
replaySubject.next(12);
replaySubject.next(13);

replaySubject.subscribe((d) => console.log(d)); // 12 , 13 , becauser we gave pass 2 in the ReplaySubject.

// (4) After completed the subject we need to get the value , so we are using AsyncSubject

const asyncSubject = new AsyncSubject(); // 2 is the latest number of value
asyncSubject.next(10);
asyncSubject.next(11); // this one
asyncSubject.complete();
asyncSubject.next(12);
asyncSubject.next(13);

asyncSubject.subscribe((d) => console.log(d)); // output will be 11 .Because before complete latest value is 11 .


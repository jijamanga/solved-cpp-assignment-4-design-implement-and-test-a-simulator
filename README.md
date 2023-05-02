Download Link: https://assignmentchef.com/product/solved-cpp-assignment-4-design-implement-and-test-a-simulator
<br>
Your university is in the process of acquiring a new supercomputer to support research activities. The IT department needs to evaluate policies for the batch job submission system, with job control and accounting. To do this, it needs a simulation tool to model the behaviour of the computing platform and to explore alternative queueing/accounting strategies.

The assignment is to design, implement and test a simulator of the new computing system.

<h1>User Requirements</h1>

The simulated computing system shall be heterogeneous, containing:

<ul>

 <li>A set of “traditional” computing nodes, i.e. shared-memory multicore CPUs;</li>

 <li>A set of “accelerated” compute nodes, same as above but with 2 attached GPUs dedicated to computations;</li>

</ul>

There shall be a total of at least 128 nodes with at least 16 processor cores per node. Among the available nodes, at least 8 shall be equipped with GPUs.

The simulated users of the system can be classified as:

<ul>

 <li>IT support;</li>

 <li>Researchers;</li>

 <li>Students;</li>

</ul>

Researchers are divided into groups, where each group has an allocation of resources, but individual researchers may have grants entitling them to additional resource usage.

Students are grouped by the curriculum they are enrolled in, and all students have a cap on the maximum usable resources, both cumulative and instantaneous, which may depend on their group.

The batch system shall match job requests to resources; there will be different classes of jobs for different uses, e.g. short, medium, long running, gpu, interactive, etc. Typically, job classes/queues are distinguished not only on the running time but also on the amount of resources that can be requested.

The job queues are maintained in an order established by an auxiliary algorithm called a scheduler; the interface to the scheduler should be designed so that it would be easy to test different algorithms. Indeed, the overall performance of the computing system in actual operation strongly depends on the scheduler, therefore the evaluation of a given scheduler is one of the most important features of the simulation.

The proper design and implementation of an efficient scheduler is a task beyond the scope of the current module; hence, for the purposes of this assignment, it is sufficient to implement and interface a simple first-come first-served scheduler, provided the interfacing mechanism is designed to allow for later experimentation with other schedulers<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>.

The policy constraints are:

<ul>

 <li>There are at least five different job queues:

  <ol>

   <li>Short, interactive jobs that can take up to 2 nodes for no more than1 hour; a certain subset (say 10%) of the machine must be reserved for this queue;</li>

   <li>Medium-sized jobs that can take up to 10% of the total number ofcores, and can last up to 8 hours; another subset (say 30%) of the machine must be reserved for this queue</li>

   <li>Large jobs, that can take up to 16 hours and up to 50% of the totalcore count;</li>

   <li>GPU, for jobs requiring nodes equipped with them;</li>

   <li>Huge, active only from 0500pm Friday to 0900am Monday, where thejobs can potentially reserve the whole machine. During these times the other job queues do not serve requests.</li>

  </ol></li>

 <li>The cost of a node-hour has one value for all normal nodes, and a different, slightly higher value for GPU-enabled nodes;</li>

 <li>Each job will request a certain number of processor cores for a certain amount of time.</li>

</ul>

The order in which the jobs are served is determined by the scheduler algorithm; as mentioned above, for the sake of simplicity you can assume a first-come first-served scheduling, with the proviso of easy maintenance/replacement;

<ul>

 <li>At the end of the week, there will be a cutoff time such that no new jobs will start if their estimated completion time will go beyond the end of the work week (thereby leaving the machine free for the weekend queue).</li>

</ul>

The machine can be assumed to have a constant operational cost per hour.

In the simulation program, users will be modeled as producers of requests, with each user having a certain budget; each user will produce requests up to his/her available budget. The exact resource requirements for each job will be created with the aid of a pseudo-random number generator. For simplicity, it is allowed (but not required) for each user to generate requests for only one job class. Within each class the amount of resources requested by each job will be modeled by a normal probability distribution; the workload request generation shall also take into account the job queue limits.

Each run of the simulator shall define a specific scenario comprising the set of simulated computer users, i.e. their number, distribution in classes and budgets. These parameters are chosen by the simulator users, i.e. the IT department staff that are investigating the policies for the new supercomputer.

During the course of the simulation, each simulated user will produce requests; the time between any two successive job requests shall be modeled by an exponential probability distribution, with parameters dependent on the class of user.

The output from the simulation should include

<ul>

 <li>The number of jobs processed in each queue (throughput) per week;</li>

 <li>The actual number of node-hours consumed by user jobs;</li>

 <li>The utilization ratio (number of node-hours consumed divided by number of node-hours available);</li>

 <li>The resulting price paid by the users;</li>

 <li>The average wait time in each queue;</li>

 <li>The average turnaround time ratio, i.e. the time from placing the job request to completion of the job divided by the actual runtime of the job;</li>

 <li>The economic balance of the centre, calculated by subtracting from the actual price the operating costs.</li>

</ul>

<h2>Assignment Requirements</h2>

The system shall be developed in either C++ or Python; it is strongly recommended that you reuse, to the extent possible, software components developed in other courses, provided you clearly identify in the accompanying and/or internal documentation which components have been reused “as is”, which have been reused with modifications, and which have been written expressely for this assignment. You shall:

<ol>

 <li>Choose appropriate models to represent the requirements (functional andnon-functional);</li>

 <li>Develop a test plan for the software. Explain what needs to be tested andhow you will implement the tests. Ensure you have adequately considered both unit and integration testing, and explain your choice of test inputs; you can use any further validation testing you think appropriate;</li>

 <li>Implement the software and run the tests from the plan, reporting theiroutput;</li>

 <li>Determine the test coverage that your test plan has achieved. Specifythe percentage coverage of statement, decision and path coverage for each component, and thereby make a statement of the coverage across your whole application.</li>

</ol>

The code shall compile and execute on Crescent; for the C++ version you are free to choose between the Intel toolchain or the GNU toolchain. You are also free to develop on your own computer as long as the final code compiles and executes correctly on Crescent.

<h2>Assignment Deliverables</h2>

Ensure that all source code can be compiled and executed, by including the relevant make/project files

<ul>

 <li>A report (to be submitted on Turnitin) containing:

  <ul>

   <li>A description of the design employed;</li>

   <li>A Software Requirements Document;</li>

   <li>A Test Plan Document;</li>

   <li>A discussion of test results and code coverage;</li>

  </ul></li>

</ul>

The report shall be submitted individually by all mebers of a group; the report shall be mostly identical, but each member will add an individual section (at the end) describing the division of work and the member’s individual contribution.

<ul>

 <li>Working Source Code with Tests (on BlackBoard, with makefiles as appropriate);</li>

</ul>

<a href="#_ftnref1" name="_ftn1">[1]</a> Note that in a real world situation the system should be used “optimally”, but different stakeholders may have different optimality criteria; for instance, users typically want to minimize waiting time, whereas administrators strive to maximize system utilization.
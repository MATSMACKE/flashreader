<template>
  <div id="reader_main">
    <div id="word-area" v-if="wordsEntered">
      <h1 id="word">
        {{word}}
      </h1>
      <p id="speed">
        {{speed}} WPM
      </p>
      <button @click="edit()" id="back">Edit Text</button>
    </div>

    <div id="textentry" v-else>
      <textarea v-model="enteredtext" name="textarea" id="textarea"></textarea>
      <button @click="read()">Start Reading</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
    msg: String
  }
})
export default class Reader extends Vue {
  wordsEntered = false
  enteredtext = `Overview
An extended essay (EE) in computer science provides students with an opportunity to investigate a particular aspect of computing and its implications for society and the world.

Within this context, they can research the latest developments and future possibilities in a rapidly changing subject that is continually breaking new barriers. There are many possible areas to be explored, each with a wealth of topics: advances in hardware and software development, comparison of the efficiency of algorithms designed to speed up data transmission or to encrypt data, network systems, computer control systems and so on.

Choice of topic
It is important that the chosen topic and its treatment reflect a firm emphasis on computing science and explores beneath the surface of this subject.

It is also important that the work goes beyond a summary of journalistic views on a particular topic. It is not sufficient for the student simply to describe new advances and developments in computing. Students are expected to analyse their findings and consider the implications.

Often, the ethical and social effects of the topic chosen will be important and may well have a part within the essay, for example in the conclusion. However, an essay that makes these considerations a major focus is not appropriate and would be better submitted as an information technology in a global society (ITGS) essay.

An in-depth analysis of trends and advances in computing should include aspects of the theory of computer science, which would necessarily demonstrate a high degree of technical knowledge and understanding.

Data for analysis may be generated from a program written by the student. This is often an appropriate method of investigation, but the code itself, and its development, will not be rewarded under the assessment criteria unless the specific techniques employed are of particular relevance to the research question.

The EE is not in any way to be confused with the computer science project that is completed as the internal assessment component for the computer science course. If the data analysed is not directly related to computer science, the EE should be registered in another, more relevant, subject.

The chosen topic may be inspired by a magazine article, an internet site, one of the case studies published in connection with computer science HL paper 3 examinations, a conversation or simply an idea that could fall into one of the following areas of interest:

aspects of the current computer science syllabus that are taken to a far greater depth than that provided in the course
current aspects of computing that are set to change or be challenged in the near future
future developments that are currently experimental but beginning to look possible
solutions to limitations that are evident in current hardware or software
comparisons between different computer systems that are actually in place.
The topic chosen should allow the student to make a full appropriate analysis, putting forward his or her own point of view.

Historical aspects of computing do not lend themselves to this treatment.

However, there may sometimes be a place for summarizing developments that have occurred until now, to put the topic in perspective or to use as a basis for predicting the future.

Availability of resources should be a consideration when deciding on a topic. The student should not choose to investigate a complex computing topic for which they have little or no access to appropriate background material or resources.

Examples of topics

These examples are just for guidance. Students must ensure their choice of topic is focused (left-hand column) rather than broad (right-hand column).


It may help for the student to start with a broad topic or area of interest, then undertake some initial secondary research before refining their topic into a more focused area and developing a preliminary research question.

Additionally, adding a statement of intent that indicates which broad process is going to be used in answering the question will help to ensure students remain focused on their research question.

Treatment of the topic
An EE in computer science is not intended as a vehicle to demonstrate programming skills. These are demonstrated in the computer science project (the internal assessment requirement of the computer science course).

The EE is an opportunity for students to be creative in a different sphere—that of independent, personal research.

While an EE may refer to a programming exercise, such as a compiler for a new language designed by the student, the emphasis in such a case should be on the design, development and analysis of the compiler and on language design. Some evaluation of the compiler in relation to those already existing is also expected.

Although program fragments may be included in the body of the EE to support the design and the discussion, the full program code (including internal documentation) should appear in an appendix as evidence.

Futuristic topics in computer science should be based on sound theory and projections of well-known computer science authorities.

Students are expected to support personal conclusions with the theories presented. This is an area where students need to be particularly careful that the analysis they apply to information gathered is their own independent analysis and that the information they use is from reliable sources.

Students are likely to turn to the internet for sources of information. When doing so, they need to verify the reliability of sources and also ensure that they are not relying too heavily on these sources to collate, rather than analyse, information.

Students are expected to both critically evaluate the resources consulted during the process of writing the essay and to expand on the material gathered from these sources in order to make any technical information understandable to a reader who might not be a specialist in the subject.

Frequent reference to the assessment criteria by both the supervisor and the student will help keep a sharper focus on the project.

Examples of topics, research questions and suggested approaches

Once students have identified their topic and written their research question, they can decide how to research their answer. They may find it helpful to write a statement outlining their broad approach. These examples are for guidance only.


An important note on “double-dipping”
Students must ensure that their EE does not duplicate other work they are submitting for the Diploma Programme.

The computer science EE and internal assessment

In particular, an EE in computer science is not an extension of the internal assessment (IA) task. Students must ensure that they understand the differences between the two.

Students are not permitted to use any of the data generated as part of their computer science solution (IA) for the EE.
Whereas the IA may focus on any aspect of computer science, an EE must not primarily be concerned with designing computer programs, although an evaluation of an existing program is permitted.
Supervisors play an important role in guiding students on these distinctions. Students risk their diploma if academic misconduct is detected.

Interpreting the EE assessment criteria
Criterion A: Focus and method
(Strands: Topic, Research question, Methodology)

The title should clearly indicate the area of research, with the underlying computer science forming the principle basis of the essay.

 Students should avoid topics that deal primarily with social aspects of information technology that would lie more within the subject ITGS (eg “The value of friendships attained through social networking sites”).

 The research question must be sharply focused in order to allow for significant research into the topic at an appropriate depth. At the same time the topic must be accessible to an IB student.

 Broad topics (eg “To what extent is the variety of different computer languages in existence beneficial or problematic for programmers”) will only lead to superficial treatment within the 4,000-word limit.

 Students should avoid choosing futuristic topics (eg “AI/robots in the next century“), which generally lead to opinion-based essays which are backed up with few facts. A journalistic approach should also be avoided as this will tend to lead to a superficial treatment of any computer science.

 The research question must be in the form of a question and should be stated in the introduction to the essay, and the areas investigated must be clearly placed in context. For example, an essay such as “How useful are neural networks in the evolution of machine learning?” must provide for the reader sufficient background information into both neural networks and machine learning.

 The student must further explain why the topic and research question are worthy choices for an EE.

 The methodology they will use to answer this question should be clearly described.

 The essay must be well planned, making use of a variety of authoritative sources. These can be taken from the internet, literature and interviews with experts in the relevant field.

 Many essays will involve an experimental or programming element, with the resulting data providing a valuable source. Students should avoid relying on small-scale surveys taken from fellow students.

Criterion B: Knowledge and understanding
(Strands: Context, Subject-specific terminology and concepts)

 The student must demonstrate their own understanding of the topic into which the essay falls.

 An essay that is comprised primarily of reworded source material will not provide this evidence. Instead the student should provide clarifications or simpler explanations of any technical information that is taken from their sources, always linking this information to the original research question.

 The source material should be selected and incorporated in a way that illustrates the knowledge gained by the student in relation to the chosen topic.

 The language must be at a technical level that is appropriate to computer science, but used in such a way that clearly demonstrates the student’s own understanding. Students should beware of making their essays over-technical and should remember that the reader will not necessarily be an expert in the specific topic that is being addressed.

Criterion C: Critical thinking
(Strands: Research, Analysis and Discussion and evaluation)

 The development of an argument that flows logically from one section to the next throughout the essay is only arrived at through sound planning.

 The student must carefully select information that is directly relevant to the research question and resist any temptation to make use of too many sources.

 The student needs to evaluate the research material not just in terms of what is relevant and necessary to support the main argument, but also in terms of the validity of the sources. This particularly applies to sources taken from the internet.

 The student should attempt to draw out conclusions wherever appropriate and not just in the concluding section of the essay.

 Any analysis of tables of results or of graphs should go further than simply translating the results into words but should look to explain the underlying reasons for the obtained results.

 Final conclusions should do more than summarize the essay but should draw the various threads together in presenting a justified answer to the original research question. The student should indicate where future research could be undertaken in order to explore unanswered questions or in expanding the original scope of the essay.

Criterion D: Presentation
(Strands: Structure, Layout)

This criterion relates to the extent to which the essay conforms to accepted academic standards in relation to how research papers should be presented. It also relates to how well these elements support the reading, understanding and evaluation of the essay.

 Students may provide a section and subsection structure to their essays, with appropriate informative headings.

Use of charts, images and tables

 Any charts, images or tables from literature sources included in the essay must be carefully selected and labelled. They should only be used if they are directly relevant to the research question, contribute towards the understanding of the argument and are of a good graphic quality.

 Large tables of raw data collected by the student are best included in an appendix, where they should be carefully labelled. Tables of processed data should be designed to clearly display the information in the most appropriate form. Graphs or charts drawn from the analysed data should be selected to highlight only the most pertinent aspects related to the argument. Too many graphs, charts and tables will distract from the overall quality of the communication.

 Only processed data that is central to the argument of the essay should be included in the body of the essay, as close as possible to its first reference. Tables should enhance a written explanation, but not themselves include significant bodies of text. If they do, then these words must be included in the word count.

 If an experimental method is long and complex, students may place the raw data in an appendix and include a summary of the methods in the body of the essay. Students who choose this option must be careful to ensure that the summary contains all elements that contribute to the quality of the investigation, since appendices are not an essential section of the EE and examiners are not required to read them. In other words, any important information that contributes to the evaluation of the method must be in the body of the essay and not the appendix. For experiments where numerical results are calculated from data obtained by changing one of the variables, it is generally good practice to show one example of the calculation in the main body of the essay. The remainder can be displayed in tabular or graphical form.

 Any material that is not original must be carefully acknowledged, with specific attention paid to the acknowledgment and referencing of quotes and ideas. This acknowledgment and referencing is applicable to audiovisual material, text, graphs and data published in print and electronic sources. If the referencing does not meet the minimum standard as indicated in the guide (name of author, date of publication, title of source and page numbers as applicable), and is not consistently applied, work will be considered as a case of possible academic misconduct.

 A bibliography is essential and has to be presented in a standard format. Title page, table of contents, page numbers, etc must contribute to the quality of presentation.

 The essay must not exceed 4,000 words of narrative. Graphs, figures, calculations, diagrams, formulas and equations are not included in the word count. Students must be aware that examiners will not read beyond the 4,000-word limit, nor assess any material presented thereafter.

Criterion E: Engagement
(Strands: Reflections on planning and progress)

This criterion assesses the student’s engagement with their research focus and the research process. It will be applied by the examiner at the end of the assessment of the essay, and is based solely on the candidate’s reflections as detailed on the RPPF, with the supervisory comments and extended essay itself as context.

 Students are expected to provide reflections on the decision-making and planning process undertaken in completing the essay. Students must demonstrate how they arrived at a topic as well as the methods and approach used. This criterion assesses the extent to which a student has evidenced the rationale for decisions made throughout the planning process and the skills and understandings developed.

For example, students may reflect on:

the approach and strategies they chose, and their relative success
the ATL skills they have developed and their effect on the student as a learner
how their conceptual understandings have developed or changed as a result of their research
challenges they faced in their research and how they overcame these
questions that emerged as a result of their research
what they would do differently if they were to undertake the research again.
 Effective reflection highlights the journey the student has engaged in through the EE process. Students must show evidence of critical and reflective thinking that goes beyond simply describing the procedures that have been followed.

 The reflections must provide the examiner with an insight into student thinking, creativity and originality within the research process. The student voice must be clearly present and demonstrate the learning that has taken place`
  read(): void {
    let tempWords = this.enteredtext.split(/[\s\n]/)
    for (let i = 0; i < tempWords.length; i++) {
      if (/\w+/.test(tempWords[i])) {
        this.words.push(tempWords[i])
      }
    }
    this.wordsEntered = true
  }

  edit(): void {
    this.pause()
    this.wordsEntered = false
  }

  playing = false

  playLoop(): void {
    if (this.playing) {
      this.wordIndex++
      setTimeout(this.playLoop, 1000/(this.speed/60))
    }
  }

  play(): void {
    this.playing = true
    this.playLoop()
  }

  pause(): void {
    this.playing = false
  }

  words: string[] = []
  wordIndex = 0
  get word(): string {
    return this.words[this.wordIndex]
  }

  speed = 600
  mounted(): void {
    document.addEventListener('keydown', (e) => {
      switch (e.key) {
        case ("ArrowUp"):
          this.speed += 25
          break
        case ("ArrowDown"):
          this.speed -= 25
          break
        case ("ArrowLeft"):
          this.wordIndex--
          break
        case ("ArrowRight"):
          this.wordIndex++
          break
        case (" "):
          if (this.playing) {
            this.pause()
          }
          else {
            this.play()
          }
          break
        case ("r"):
          this.wordIndex = 0
          break
      }
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}
#textentry {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
#reader-main {
  margin: 0;
}
#word-area {
  display: flex;
  flex-direction: column;
  flex: 4 1 1;
  align-items: center;
  justify-content: center;
}
#word {
  margin-top: 10%;
}
textarea {
  width: 75%;
  height: 75%;
  resize: none;
}
button {
  padding: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
  background-color: white;
  border: solid 2px black;
  border-radius: 10px;
  margin: 10px;
  cursor: pointer;
}
</style>

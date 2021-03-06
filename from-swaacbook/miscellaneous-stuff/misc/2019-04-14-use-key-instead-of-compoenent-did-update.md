
# Table of Contents

1.  [TIL: Use key instead of componentDidUpdate](#orge7943a0)
    1.  [an example](#org4906cf7)

\#+COMMENT -**- time-stamp-line-limit: 12; time-stamp-count: 2 -**-


<a id="orge7943a0"></a>

# TIL: Use key instead of componentDidUpdate

-   last update: Time-stamp: <span class="timestamp-wrapper"><span class="timestamp">&lt;2018-09-16 Sun 14:32&gt;</span></span>
-   capture date: <span class="timestamp-wrapper"><span class="timestamp">[2019-04-19 Fri 19:07]</span></span>
-   keywords: react, componentDidUpdate, key prop

Watching Ryan Florence over at [reacttraining.com](https://www.reacttraining.com) in the [Reach Catchup componentWillReceiveProps video](https://courses.reacttraining.com/courses/354571/lectures/5449516), towards the end, after explaining how to use `componentDidUpdate` to retrieve updated props / state based on a new prop, he then goes on to say you can do this a lot easier by setting the component's `key` to the thing you're checking in `cDU` and just make React create a whole new instance.

This is so easy it's just astounding how much it makes sense.


<a id="org4906cf7"></a>

## an example

Let's say you have a collection of notes to display, with the following structure:

    {
      "notes": [
        {
          "id": Int,
          "body": String,
          "createdAt": String,
          "updatedAt": String,
          "creator": {
    	"name": String
          },
          "public": Boolean
        }
      ]
    }

Let's say this is our component:

    const Notes = ({ notes }) => (
      <NoteList>
        {notes && notes.length > 0 ? (
          notes.map((note, index) => <Note key={index} note={note} />)
        ) : (
          <NoNotes />
        )}
      </NoteList>
    )

If for some reason you need to manage state for each note, perhaps because you're modifying it in place (i.e. within the row), or you delete a note, or add a note, you might need to keep the state updated based on update props. If the note changes, you may need to perform refetch to get the updated info.

Or so you might think.

Instead, by using the `note.id` as the `key`, you can easily make React produce a new instance.

    const Notes = ({ notes }) => (
      <NoteList>
        {notes && notes.length > 0 ? (
          notes.map(note => <Note key={note.id} note={note} />)
        ) : (
          <NoNotes />
        )}
      </NoteList>
    )

If the id of the particular note in that sequence changes, React will re-instantiate the `Note` and whatever you do to initialize it is done with the new note.

This may not be the best example, but the concept is what's important for me to remember. I have a habit of just using the map index instead of something more useful to React.


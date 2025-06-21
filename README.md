# E-Library Semantic Search

This project models an E-Library system using semantic web technologies and RDF/OWL ontologies. It organizes books, authors, publishers, and topics, enabling advanced semantic relationships and queries.

## 1. Overview

The ontology enables:
- Tracking authorship and co-authorship
- Managing publication metadata (ISBN, format, language)
- Defining hierarchical topic classifications

## 2. Class Hierarchy and Relationships

**Classes:**
- **Book**: Represents books
- **Author**: Writers of books
- **Publisher**: Organizations/individuals publishing works
- **Format**: File/print formats (e.g., PDF)
- **Topic**: Hierarchical categories (e.g., "Artificial Intelligence" is a subtopic of "Computer Science")

**Relationships:**
- Books are written by Authors and published by Publishers
- Books have Formats and Topics
- Topics can be organized hierarchically (subtopics)

## 3. Properties

### 3.1 Object Properties
| Property      | Domain   | Range    | Description                                 |
|--------------|----------|----------|---------------------------------------------|
| authorOf     | Author   | Book     | Author of a book/article                    |
| coAuthorOf   | Author   | Author   | Co-authorship between authors               |
| hasFormat    | Book     | Format   | Format of the publication (e.g., PDF)       |
| hasTopic     | Book     | Topic    | Topic associated with the work              |
| publishedBy  | Book     | Publisher| Publisher of the work                      |
| subTopicOf   | Topic    | Topic    | Hierarchical relationship between topics    |
| writtenBy    | Book     | Author   | Inverse of authorOf                        |

### 3.2 Data Properties
| Property         | Domain | Range (XSD) | Description                  |
|-----------------|--------|-------------|------------------------------|
| ISBN            | Book   | integer     | Unique identifier for books  |
| language        | Book   | language    | Language of the work         |
| pageCount       | Book   | integer     | Number of pages              |
| publicationYear | Book   | dateTime    | Publication date             |

## 4. Example Instances

- **1984 (Book)**
  - hasTopic: Dystopian
  - writtenBy: George_Orwell
  - publishedBy: Secker_Warburg
  - ISBN: 9780451524935
- **The_Prophet (Book)**
  - hasFormat: Paperback
  - publishedBy: Kahlil_Gibran
- **Knowledge_Graphs_101 (Book)**
  - hasTopic: Knowledge_Graph (subtopic of Artificial_Intelligence)

## 5. Inferred Semantics and Rules

### 5.1 SWRL Rules
- **Topic Inheritance**: A book with subtopic Knowledge_Graph automatically inherits Artificial_Intelligence.
- **Author of Books**: A book with an author inferred as the author of that book automatically.
- **Publisher of Books**: A book published by a publisher inferred as the publisher of that book automatically.
- **CoAuthor of Books**: Authors who have collaborated on the same book inferred as co-authors automatically.

### 5.2 SPARQL Queries
- **List Topics and Their Subtopics**: Shows which topics are subtopics of broader topics (e.g., "Artificial_Intelligence" is a subtopic of "Computer_Science").
- **Get Book Details**: Lists books with their ISBN, page count, and publication year.
- **Find Books Published by MIT Press**: Returns all books published by "MIT_Press" (e.g., "Semantic_Web_Primer").
- **Show All Book Formats**: Lists unique formats (e.g., PDF) available for books.
- **Books Tagged Under "Computer_Science"**: Finds books directly linked to the "Computer_Science" topic.

## 6. Visual Diagrams

See the presentation for class hierarchy and relationship diagrams.

## Repository Contents
- **E-Library Semantic Search.rdf**: The ontology file (RDF/XML)
- **E-Library documentation.docx**: Project documentation
- **E-Library presentation.pptx**: Project presentation

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/JinxX404/E-Library-Semantic-Search.git
   ```
2. Open the RDF file with [Protégé](https://protege.stanford.edu/) or similar tools.
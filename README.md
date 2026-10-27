# library-management-system
REPORT ztest.

CLASS book DEFINITION.

  PUBLIC SECTION.

    DATA book_id TYPE i.
    DATA book_name TYPE string.
    DATA author TYPE string.
    DATA status TYPE string.

    METHODS constructor
      IMPORTING
        iv_book_id TYPE i
        iv_book_name TYPE string
        iv_author TYPE string
        iv_status TYPE string.

    METHODS display_book.
    METHODS issue_book.
    METHODS return_book.
    METHODS check_availability.

ENDCLASS.


CLASS book IMPLEMENTATION.

  METHOD constructor.

    book_id = iv_book_id.
    book_name = iv_book_name.
    author = iv_author.
    status = iv_status.

  ENDMETHOD.


  METHOD display_book.

    WRITE: / 'Book ID:', book_id.
    WRITE: / 'Book Name:', book_name.
    WRITE: / 'Author:', author.
    WRITE: / 'Status:', status.

  ENDMETHOD.


  METHOD issue_book.

    IF status = 'Available'.

      status = 'Issued'.

      WRITE: / 'Book is issued'.

    ELSE.

      WRITE: / 'Book is not available'.

    ENDIF.

  ENDMETHOD.


  METHOD return_book.

    IF status = 'Issued'.

      status = 'Available'.

      WRITE: / 'Book returned successfully'.

    ELSE.

      WRITE: / 'Book is already available'.

    ENDIF.

  ENDMETHOD.


  METHOD check_availability.

    IF status = 'Available'.

      WRITE: / 'Book is available'.

    ELSE.

      WRITE: / 'Book is not available'.

    ENDIF.

  ENDMETHOD.

ENDCLASS.


START-OF-SELECTION.

  DATA obj TYPE REF TO book.

  CREATE OBJECT obj
    EXPORTING
      iv_book_id = 100
      iv_book_name = 'ABAP'
      iv_author = 'John'
      iv_status = 'Available'.

  obj->display_book( ).

  obj->check_availability( ).

  obj->issue_book( ).

 

  obj->return_book( ).

 

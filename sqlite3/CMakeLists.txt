add_definitions(
   # See: https://www.sqlite.org/compile.html

   # Defaults from OSS Osquery
  -DSQLITE_ENABLE_COLUMN_METADATA
  -DSQLITE_SECURE_DELETE
  -DSQLITE_ENABLE_UNLOCK_NOTIFY
  -DSQLITE_ENABLE_DBSTAT_VTAB
  -DSQLITE_ENABLE_JSON1
  -DSQLITE_ENABLE_PREUPDATE_HOOK
  -DSQLITE_ENABLE_SESSION
  -DSQLITE_SOUNDEX

   # Carry over from Osquery 3.x
  -DSQLITE_ENABLE_API_ARMOR
  -DSQLITE_ENABLE_MEMORY_MANAGEMENT
  # Functionality disables
  -DSQLITE_DISABLE_LFS
  -DSQLITE_DISABLE_DIRSYNC
  -DSQLITE_DISABLE_FTS3_UNICODE
  -DSQLITE_DISABLE_FTS4_DEFERRED
  -DSQLITE_OMIT_AUTHORIZATION
  -DSQLITE_OMIT_DEPRECATED
  -DSQLITE_OMIT_SHARED_CACHE
  # Omitting the WAL will prevent database file access.
  #-DSQLITE_OMIT_WAL
  -DSQLITE_OMIT_LOOKASIDE
)

if(NOT WIN32)
  add_compile_options(
    -Wno-parentheses-equality
    -Wno-unused-value
  )
endif()

add_library(osquery_sqlite OBJECT sqlite3.c)

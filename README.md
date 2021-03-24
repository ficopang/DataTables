# DataTables
Fix DataTables SSP Search

Line 361, causes error `DataTables warning: table id=example - An SQL error occurred: SQLSTATE[HY093]: Invalid parameter number: number of bound variables does not match number of tokens`

    $resTotalLength = self::sql_exec( $db, $bindings,
			"SELECT COUNT(`{$primaryKey}`)
			 FROM   `$table` ".
			$whereAllSql
		);
    
Replace with this to fix

		$resTotalLength = self::sql_exec( $db,
			"SELECT COUNT(`{$primaryKey}`)
			 FROM   `$table` ".
			$whereAllSql
		);

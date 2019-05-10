---
title: SDK for Java の拡張機能 - SQL Server の言語拡張機能
description: Microsoft SQL Server 2019 の Microsoft 拡張機能 SDK for Java の説明
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c244d67c7f1cd1636fcd2de0b80454c96927b5d7
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65101820"
---
# <a name="microsoft-extensibility-sdk-for-java-for-sql-server"></a>Microsoft SDK for Java の SQL Server の機能拡張

SQL Server CTP 2.5 では、Java 用の Microsoft 拡張機能 SDK を使用して SQL Server を Java プログラムを実装できます。 これは、Java 言語拡張機能を使用して SQL Server にデータを交換し、SQL Server からの Java コードを実行するためのインターフェイスです。

> [!Note]
> CTP 2.5 では、SDK は、以前の Ctp から大きな変更です。 作業をしたサンプルは、代わりに、SDK を使用して更新する必要があります。

ダウンロード、 [Microsoft 拡張機能 SDK for Microsoft SQL Server 用の Java](http://aka.ms/mssql-java-lang-extension)します。

## <a name="implementation-requirements"></a>実装要件

SDK インターフェイスでは、一連の Java ランタイムと通信する SQL Server の処理を完了する必要がある要件を定義します。 つまり、メイン クラスには、いくつか実装規則に従う必要があります。 SQL Server は、Java 言語の拡張機能を使用する Java クラスと exchange データの特定のメソッドを実行できます。

SDK を使用する方法の例は、次を参照してください。、[エンド ツー エンドのサンプル](java-first-sample.md)します。

## <a name="sdk-classes"></a>SDK クラス

この SDK は、3 つのクラスで構成されます。

SQL Server でのデータを交換する Java 拡張機能インターフェイスを定義する 2 つの抽象クラスを使用します。

- **AbstractSqlServerExtensionExecutor**
- **AbstractSqlServerExtensionDataset**

3 番目のクラスは、データ セット オブジェクトの実装を含むヘルパー クラスです。 これは、クラスは省略可能なクラスを使用して開始するが簡単にします。 このようなクラスの独自の実装を使用することができます。

- **PrimitiveDataset**

以下の SQL Server の詳細と Java 言語の拡張機能では、各クラスのソース コードに従います。

## <a name="abstractsqlserverextensionexecutor"></a>AbstractSqlServerExtensionExecutor

これは、SQL Server の Java コードを実行する Java 言語の拡張機能によって使用されるインターフェイスを含む抽象クラスです。

メイン Java クラスは、このクラスから継承する必要があります。 このクラスから継承することで、独自のクラスを実装する必要があるクラスで特定のメソッドがあることを意味します。

この抽象クラスを継承するには、クラスの宣言で抽象クラスの名前を持つ拡張します。

```java
public class <MyClass> extends AbstractSqlServerExtensionExecutor {}
```

少なくとも、メイン クラスは execute(...) メソッドを実装する必要があります。

### <a name="method-execute"></a>メソッドを実行します。

Execute メソッドは、SQL Server からの Java コードを呼び出す、Java 言語拡張機能を使用して SQL Server から呼び出されるメソッドです。 必要がありますとして表示するこの重要なメソッドがメインが含まれてから SQL Server を実行する操作。

SQL Server から Java にメソッドの引数を渡すを使用して、 `@param` sp_execute_external_script のパラメーター。 メソッド**実行**これにより、引数を受け取る。

```java
public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params)  {}
```

### <a name="method-init"></a>メソッドの初期化

Init メソッドは、コンス トラクターの後と、execute メソッドの前に実行されます。 このメソッドでは、execute(...) する前に実行する必要があるすべての操作を実行できます。

```java
public void init(String sessionId, int taskId, int numtask) {}
```

### <a name="abstractsqlserverextensionexecutor-source-code"></a>AbstractSqlServerExtensionExecutor ソース コード

詳細については、ソース コードを以下の参照できます。

```java
package com.microsoft.sqlserver.javalangextension;

import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionDataset;
import java.lang.UnsupportedOperationException;
import java.util.LinkedHashMap;

/**
 * Abstract class containing interface used by the Java extension
 */
public abstract class AbstractSqlServerExtensionExecutor {
    /* Supported versions of the Java extension */
    public final int SQLSERVER_JAVA_LANG_EXTENSION_V1 = 1;

    /* Members used by the extension to determine application specifics */
    protected int executorExtensionVersion;
    protected String executorInputDatasetClassName;
    protected String executorOutputDatasetClassName;

    public AbstractSqlServerExtensionExecutor() { }

    public void init(String sessionId, int taskId, int numTasks) {
        /* Default implementation of init() is no-op */
    }

    public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params) {
        throw new UnsupportedOperationException("AbstractSqlServerExtensionExecutor execute() is not implemented");
    }

    public void cleanup() {
        /* Default implementation of cleanup() is no-op */
    }
}
```

### <a name="abstractsqlserverextensiondataset"></a>AbstractSqlServerExtensionDataset

Java 拡張機能によって使用される入力と出力のデータを処理するためのインターフェイスを含む抽象クラスです。

```java
package com.microsoft.sqlserver.javalangextension;

import java.lang.UnsupportedOperationException;

/**
 * Abstract class containing interface for handling input and output data used by the Java
 * extension.
 */
public class AbstractSqlServerExtensionDataset {
    /**
     * Column metadata interfaces
     */
    public void addColumnMetadata(int columnId, String columnName, int columnType, int precision, int scale) {
        throw new UnsupportedOperationException("addColumnMetadata is not implemented");
    }

    public int getColumnCount() {
        throw new UnsupportedOperationException("getColumnCount is not implemented");
    }

    public String getColumnName(int columnId) {
        throw new UnsupportedOperationException("getColumnName is not implemented");
    }

    public int getColumnPrecision(int columnId) {
        throw new UnsupportedOperationException("getColumnPrecision is not implemented");
    }

    public int getColumnScale(int columnId) {
        throw new UnsupportedOperationException("getColumnScale is not implemented");
    }

    public int getColumnType(int columnId) {
        throw new UnsupportedOperationException("getColumnNullMap is not implemented");
    }

    public boolean[] getColumnNullMap(int columnId) {
        throw new UnsupportedOperationException("getColumnNullMap is not implemented");
    }

    /**
     * Adding column interfaces
     */
    public void addIntColumn(int columnId, int[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addIntColumn is not implemented");
    }

    public void addBooleanColumn(int columnId, boolean[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addBooleanColumn is not implemented");
    }

    public void addLongColumn(int columnId, long[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addLongColumn is not implemented");
    }

    public void addFloatColumn(int columnId, float[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addFloatColumn is not implemented");
    }

    public void addDoubleColumn(int columnId, double[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addDoubleColumn is not implemented");
    }

    public void addShortColumn(int columnId, short[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addShortColumn is not implemented");
    }

    public void addStringColumn(int columnId, String[] rows) {
        throw new UnsupportedOperationException("addStringColumn is not implemented");
    }

    public void addBinaryColumn(int columnId, byte[][] rows) {
        throw new UnsupportedOperationException("addBinaryColumn is not implemented");
    }

    /**
     * Retrieving column interfaces
     */
    public int[] getIntColumn(int columnId) {
        throw new UnsupportedOperationException("getIntColumn is not implemented");
    }

    public long[] getLongColumn(int columnId) {
        throw new UnsupportedOperationException("getLongColumn is not implemented");
    }

    public float[] getFloatColumn(int columnId) {
        throw new UnsupportedOperationException("getFloatColumn is not implemented");
    }

    public short[] getShortColumn(int columnId) {
        throw new UnsupportedOperationException("getShortColumn is not implemented");
    }

    public boolean[] getBooleanColumn(int columnId) {
        throw new UnsupportedOperationException("getBooleanColumn is not implemented");
    }

    public double[] getDoubleColumn(int columnId) {
        throw new UnsupportedOperationException("getDoubleColumn is not implemented");
    }

    public String[] getStringColumn(int columnId) {
        throw new UnsupportedOperationException("getStringColumn is not implemented");
    }

    public byte[][] getBinaryColumn(int columnId) {
        throw new UnsupportedOperationException("getBinaryColumn is not implemented");
    }
}
```

### <a name="primitivedataset"></a>PrimitiveDataset

このクラスの実装は、 **AbstractSqlServerExtensionDataset**プリミティブ配列として単純型を格納します。 使用する省略可能なヘルパー クラスとして単に、SDK で提供されます。

このクラスを使用しない場合から継承するクラスを実装する必要があります。 **AbstractSqlServerExtensionDataset**します。  

```java
package com.microsoft.sqlserver.javalangextension;

import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionDataset;
import java.lang.IllegalArgumentException;
import java.util.HashMap;
import java.util.Map;
import java.util.Map.Entry;

/**
 * Implementation of AbstractSqlServerExtensionDataset that stores
 * simple types as primitives arrays
 */
public class PrimitiveDataset extends AbstractSqlServerExtensionDataset {
    Map<Integer, String>  columnNames;
    Map<Integer, Integer> columnTypes;
    Map<Integer, Integer> columnPrecisions;
    Map<Integer, Integer> columnScales;
    Map<Integer, Object>  columns;
    Map<Integer, boolean[]> columnNullMaps;

    public PrimitiveDataset() {
        columnTypes = new HashMap<>();
        columnNames = new HashMap<>();
        columnPrecisions = new HashMap<>();
        columnScales = new HashMap<>();
        columns = new HashMap<>();
        columnNullMaps = new HashMap<>();
    }

    /**
     * Column metadata interfaces. Metadata is stored in a hash map, using the column ID as the key
     */
    public void addColumnMetadata(int columnId, String columnName, int sqlType, int precision, int scale) {
        if (columnTypes.containsKey(columnId))
        {
            throw new IllegalArgumentException("Metadata for column ID #: " + columnId + " already exists");
        }

        columnTypes.put(columnId, sqlType);
        columnNames.put(columnId, columnName);
        columnPrecisions.put(columnId, precision);
        columnScales.put(columnId, scale);
    }

    public int getColumnCount() {
        return columnTypes.size();
    }

    public String getColumnName(int columnId) {
        checkColumnMetadata(columnId);
        return columnNames.get(columnId);
    }

    public int getColumnPrecision(int columnId) {
        checkColumnMetadata(columnId);
        return columnPrecisions.get(columnId).intValue();
    }

    public int getColumnScale(int columnId) {
        checkColumnMetadata(columnId);
        return columnScales.get(columnId).intValue();
    }

    public int getColumnType(int columnId) {
        checkColumnMetadata(columnId);
        return columnTypes.get(columnId).intValue();
    }

    public boolean[] getColumnNullMap(int columnId) {
        checkColumnMetadata(columnId);
        return columnNullMaps.get(columnId);
    }

    /**
     * Adding column data interfaces. Column data is stored in a hash map, using the column ID as the key and
     * an array of the corresponding type representing each row. Primitives cannot be null, thus null values
     * are represented by an additional boolean array containing a flag to indicate if that value is null.
     * A null indicator array indicates that there are no null values in that column.
     */
    public void addIntColumn(int columnId, int[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addBooleanColumn(int columnId, boolean[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    };

    public void addLongColumn(int columnId, long[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addFloatColumn(int columnId, float[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addDoubleColumn(int columnId, double[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addShortColumn(int columnId, short[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addStringColumn(int columnId, String[] rows) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
    }

    public void addBinaryColumn(int columnId, byte[][] rows) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
    }

    /**
     * Retreiving column data interfaces. For primitive types, calling getColumnNullMap() for the column ID
     * will return the boolean array indicating null values.
     */
    public int[] getIntColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (int[])columns.get(columnId);
    }

    public long[] getLongColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (long[])columns.get(columnId);
    }

    public float[] getFloatColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (float[])columns.get(columnId);
    }

    public short[] getShortColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (short[])columns.get(columnId);
    }

    public boolean[] getBooleanColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (boolean[])columns.get(columnId);
    }

    public double[] getDoubleColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (double[])columns.get(columnId);
    }

    public String[] getStringColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (String[])columns.get(columnId);
    }

    public byte[][] getBinaryColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (byte[][])columns.get(columnId);
    }

    private void checkColumnMetadata(int columnId)
    {
        if (!columnTypes.containsKey(columnId)) {
            throw new IllegalArgumentException("Metadata for column ID #: " + columnId + " does not exist");
        }
    }
}
```

## <a name="next-steps"></a>次のステップ

+ [エンド ツー エンドの SDK を使用して Java サンプル](java-first-sample.md)
+ [SQL Server で Java を呼び出す方法](howto-call-java-from-sql.md)
+ [SQL Server での Java 拡張機能](extension-java.md)
+ [Java および SQL Server データ型](java-sql-datatypes.md)

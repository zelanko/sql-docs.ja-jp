---
title: "以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "前のバージョン [SQL Server], データ形式のインポートとエクスポート"
  - "-V スイッチ"
  - "データ形式 [SQL Server], 以前のバージョン"
  - "以前のバージョン [SQL Server], データ形式のインポートとエクスポート"
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
caps.latest.revision: 40
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 40
---
# 以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、**bcp** を使用すると、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] からネイティブ形式データおよび文字形式データを **-V** スイッチを指定してインポートすることができます。 **-V** スイッチを使用すると、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は指定された以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型を使用し、データ ファイル形式はその以前のバージョンのものと同じになります。  
  
 データ ファイルに以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンを指定するには、**-V** スイッチと次のいずれかの修飾子を使用します。  
  
|SQL Server のバージョン|Qualifier|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|**-V80**|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|**-V90**|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|**-V100**|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|**-V 110**|  
  
## データ型について  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、いくつかの新しいデータ型がサポートされるようになりました。 以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンに新しいデータ型をインポートする場合は、古い **bcp** クライアントで読み取ることが可能な形式でそのデータ型を格納する必要があります。 次の表では、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との互換性を維持するために、新しいデータ型がどのように変換されるかをまとめています。  
  
|SQL Server 2005 の新しいデータ型|バージョン 6*x*の互換性のあるデータ型|バージョン 70 の互換性のあるデータ型|バージョン 80 の互換性のあるデータ型|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|**bigint**|**decimal**|**decimal**|*|  
|**sql_variant**|**text**|**nvarchar (4000)**|*|  
|**varchar(max)**|**text**|**text**|**text**|  
|**nvarchar(max)**|**ntext**|**ntext**|**ntext**|  
|**varbinary(max)**|**image**|**image**|**image**|  
|XML|**ntext**|**ntext**|**ntext**|  
|UDT**|**image**|**image**|**image**|  
  
 * この型はネイティブでサポートされています。  
  
 ** UDT はユーザー定義型を示します。  
  
## –V 80 を使用したエクスポート  
 **–V80** スイッチを使用してデータを一括エクスポートする場合、**nvarchar(max)**、**varchar(max)**、**varbinary(max)**、 型のデータ、XML データ、およびネイティブ モードの UDT データは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンの既定である 8 バイトのプレフィックスではなく、**text**、**image**、および **ntext** 型のデータと同様に、4 バイトのプレフィックス付きで格納されます。  
  
## 日付値のコピー  
 **bcp** は ODBC 一括コピー API を使用します。 したがって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、**bcp** に日付値をインポートするには、ODBC の日付形式 (*yyyy-mm-dd hh:mm:ss*[*.f...*]) を使用します。  
  
 **bcp** コマンドでは、 **datetime** 型と **smalldatetime** 型の値に使用される ODBC の既定の形式を使用して、文字形式のデータ ファイルがエクスポートされます。 たとえば、日付 `12 Aug 1998` が含まれた **datetime** 型の列は、文字列 `1998-08-12 00:00:00.000` としてデータ ファイルに一括コピーされます。  
  
> [!IMPORTANT]  
>  **bcp** を使用してデータを **smalldatetime**フィールドにインポートする場合は、秒の値が 00.000 になっていることを確認してください。それ以外の場合、この操作は失敗します。 **smalldatetime** データ型には、最も近い "分" までの値のみが保持されます。 この場合、BULK INSERT および INSERT ... SELECT * FROM OPENROWSET(BULK...) は失敗しませんが、秒の値は切り捨てられます。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **一括インポートまたは一括エクスポートのデータ形式を使用するには**  
  
-   [文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## 参照  
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [SQL Server データベース エンジンの旧バージョンとの互換性](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
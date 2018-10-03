---
title: についてのデータ型の違い |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 546dc71fad06fc69d816d16c1d6c2d67f59f968b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773210"
---
# <a name="understanding-data-type-differences"></a>データ型の違いについて

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Java プログラミング言語のデータ型と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型には、異なる点が多数あります。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、さまざまな型の変換を行うことによって、これらの違いに対応しています。  

## <a name="character-types"></a>文字型

JDBC の文字の文字列データ型は**CHAR**、 **VARCHAR**、および**LONGVARCHAR**します。 JDBC ドライバーでは、JDBC 4.0 API がサポートされます。 JDBC 4.0 では、JDBC の文字の文字列データ型をすることできますも**NCHAR**、 **NVARCHAR**、および**LONGNVARCHAR**します。 これらの新しい文字列型では Java のネイティブの文字型が Unicode 形式で維持されるため、ANSI から Unicode への変換または Unicode から ANSI への変換を実行する必要がありません。  
  
| 型            | [説明]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 固定長    | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Char**と**nchar**データ型は JDBC に直接マップ**CHAR**と**NCHAR**型。 列が `SET ANSI_PADDING ON` の場合、このサーバーが埋め込みを行う固定長の型です。 埋め込みは **nchar** に対しては常にオンですが、**char** に対しては、サーバーにより char 列の埋め込みが行われていない場合は、JDBC ドライバーが埋め込みを行います。                                                                                                                                                                                                                                                                                                                                                                                      |
| 可変長 | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Varchar**と**nvarchar**型 JDBC に直接マップ**VARCHAR**と**NVARCHAR**それぞれの型します。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Long            | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **テキスト**と**ntext**型は JDBC にマップ**LONGVARCHAR**と**LONGNVARCHAR**それぞれ入力します。 以降では非推奨の型のうち[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、大きな値型を使用する必要がありますので、 **varchar (max)** または**nvarchar (max)** を代わりにします。<br /><br /> 更新プログラムを使用して\<数値型 > と[updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md)に対してメソッドが失敗**テキスト**と**ntext** server 列。 ただし、サーバーの **text** 列と **ntext** 列に対して、文字変換の型を指定して [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) メソッドを使用することは可能です。 |
  
## <a name="binary-string-types"></a>バイナリ文字列型

JDBC のバイナリ文字列型は**バイナリ**、 **VARBINARY**、および**LONGVARBINARY**します。  
  
| 型            | [説明]                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 固定長    | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **バイナリ**JDBC に直接マップ」と入力**バイナリ**型。 列が SET ANSI_PADDING ON の場合、これはサーバーが埋め込みを行う固定長の型です。 サーバーの char 列に埋め込みが行われていない場合は、JDBC ドライバーが埋め込みを行います。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **タイムスタンプ**型は、JDBC**バイナリ**8 バイトの固定長を持つ型。 |
| 可変長 | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Varbinary** JDBC にマップ**VARBINARY**型。<br /><br /> **Udt**入力[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]として JDBC にマップされます、 **VARBINARY**型。                                                                                                                                                                                                                                 |
| Long            | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **イメージ**JDBC にマップ**LONGVARBINARY**型。 この型は [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では非推奨とされるため、代わりに大きな値の型である **varbinary(max)** を使用する必要があります。                                                                                                                                                                                           |
  
## <a name="exact-numeric-types"></a>真数型

JDBC の真数型は、対応する SQL Server 型に直接マップされます。  
  
| 型     | [説明]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT      | JDBC の **BIT** 型は、0 または 1 の単一ビットを表します。 これにマップする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**ビット**型。                                                                                                                                                                                                                                                                                                                                       |
| TINYINT  | JDBC の **TINYINT** 型は、1 バイトを表します。 これにマップする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint**型。                                                                                                                                                                                                                                                                                                                                                 |
| SMALLINT | JDBC の **SMALLINT** 型は、符号付きの 16 ビット整数を表します。 これにマップする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **smallint**型。                                                                                                                                                                                                                                                                                                                                     |
| INTEGER  | JDBC の **INTEGER** 型は、符号付きの 32 ビット整数を表します。 これにマップする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **int**型。                                                                                                                                                                                                                                                                                                                                           |
| bigint   | JDBC の **BIGINT** 型は、符号付きの 64 ビット整数を表します。 これにマップを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bigint**型。                                                                                                                                                                                                                                                                                                                                         |
| NUMERIC  | JDBC の **NUMERIC** 型は、同一有効桁数の値を保持する固定長の有効桁数の 10 進値を表します。 **数値**型にマップされます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **数値**型。                                                                                                                                                                                                                                                                   |
| [DECIMAL]  | JDBC の **DECIMAL** 型は、指定された有効桁数以上の値を保持する固定長の有効桁数の 10 進値を表します。 **DECIMAL**型にマップされます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **decimal**型。<br /><br /> JDBC の **DECIMAL** 型は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **money** 型と **smallmoney** 型にもマップされます。これらはそれぞれ、8 バイトと 4 バイトで格納される固定長の有効桁数の decimal 型です。 |
  
## <a name="approximate-numeric-types"></a>概数型

JDBC の概数の数値型には**実際**、**二重**、および**FLOAT**します。  
  
| 型   | [説明]                                                                                                                                                                                                                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| real   | JDBC の **REAL** 型の有効桁数は 7 桁 (単精度) で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **real** 型に直接マップされます。                                                                                                                                     |
| DOUBLE | JDBC の **DOUBLE** 型の有効桁数は 15 桁 (倍精度) で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **float** 型にマップされます。 JDBC **FLOAT**型のシノニムになって**二重**します。 混同ができるので**FLOAT**と**二重**、**二重**をお勧めします。 |
  
## <a name="datetime-types"></a>Datetime 型

JDBC**タイムスタンプ**型にマップされます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**と**smalldatetime**型。 **datetime** 型は、2 つの 4 バイト整数に格納されます。 **smalldatetime** 型は同じ情報 (日付と時刻) を保持しますが、精度が低く、2 つの 2 バイトの小整数に格納されます。  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **timestamp** 型は、固定長のバイナリ文字列型です。 JDBC の時刻型のいずれかにマップされない:**日付**、**時間**、または**タイムスタンプ**します。  
  
## <a name="custom-type-mapping"></a>カスタム型のマッピング

JDBC の sql データ インターフェイスを使用するカスタム型のマッピング機能では、型 (Udt、Struct など) が高度な。 JDBC driver では実装されていません。  
  
## <a name="see-also"></a>参照

[JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  

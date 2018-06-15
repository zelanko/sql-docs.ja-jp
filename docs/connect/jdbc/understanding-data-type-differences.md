---
title: についてのデータ型の違い |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5395b915d2f261813495d364730d0442a8139334
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853317"
---
# <a name="understanding-data-type-differences"></a>データ型の違いについて
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Java プログラミング言語のデータ型間の相違点の数があると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]さまざまな種類の変換によって、これらの違いを容易にするために役立ちます。  
  
## <a name="character-types"></a>文字型  
 JDBC の文字列データ型は**CHAR**、 **VARCHAR**、および**LONGVARCHAR**です。 JDBC ドライバーでは、JDBC 4.0 API がサポートされます。 JDBC 4.0 では、JDBC の文字列データ型は指定できますも**NCHAR**、 **NVARCHAR**、および**LONGNVARCHAR**です。 これらの新しい文字列型では Java のネイティブの文字型が Unicode 形式で維持されるため、ANSI から Unicode への変換または Unicode から ANSI への変換を実行する必要がありません。  
  
|型|Description|  
|----------|-----------------|  
|固定長|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Char**と**nchar**データ型は JDBC に直接マップ**CHAR**と**NCHAR**型です。 列が SET ANSI_PADDING ON の場合、これらはサーバーが埋め込みを行う固定長の型です。 パディングは常にオンに**nchar**が**char**サーバーの char 型の列が行われていない場合は、JDBC ドライバーが埋め込み。|  
|可変長|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Varchar**と**nvarchar**型 JDBC に直接マップ**VARCHAR**と**NVARCHAR**型、それぞれします。|  
|Long|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**テキスト**と**ntext**型 JDBC にマップされる**LONGVARCHAR**と**LONGNVARCHAR**それぞれ入力します。 以降で非推奨の種類が[!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]、大きな値型を使用する必要がありますので、 **varchar (max)** または**nvarchar (max)**、代わりにします。<br /><br /> 更新プログラムを使用して\<数値型 > と[updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md)に対してメソッドが失敗**テキスト**と**ntext** server 列です。 ただしを使用して、 [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)に対して指定した文字変換の型を持つメソッドはサポートされて**テキスト**と**ntext** server 列です。|  
  
## <a name="binary-string-types"></a>バイナリ文字列型  
 JDBC のバイナリ文字列型は**バイナリ**、 **VARBINARY**、および**LONGVARBINARY**です。  
  
|型|Description|  
|----------|-----------------|  
|固定長|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**バイナリ**JDBC に直接マップ」と入力**バイナリ**型です。 列が SET ANSI_PADDING ON の場合、これはサーバーが埋め込みを行う固定長の型です。 サーバーの char 列に埋め込みが行われていない場合は、JDBC ドライバーが埋め込みを行います。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**タイムスタンプ**型は、JDBC**バイナリ**8 バイトの固定長を持つ型。|  
|可変長|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Varbinary** JDBC にマップ**VARBINARY**型です。<br /><br /> **Udt**に入力[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]として JDBC にマップする**VARBINARY**型です。|  
|Long|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**イメージ**JDBC にマップ**LONGVARBINARY**型です。 この型は以降では使用されなくなりました[!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]大きな値の型を使用する必要がありますので、 **varbinary (max)** 代わりにします。|  
  
## <a name="exact-numeric-types"></a>真数型  
 JDBC の真数型は、対応する SQL Server 型に直接マップされます。  
  
|型|Description|  
|----------|-----------------|  
|BIT|JDBC**ビット**型を表す単一ビットを 0 または 1 を指定できます。 これはマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**ビット**型です。|  
|TINYINT|JDBC **TINYINT**型は、1 バイトを表します。 これにマップする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **tinyint**型。|  
|SMALLINT|JDBC **SMALLINT**型は符号付き 16 ビット整数を表します。 これにマップする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **smallint**型です。|  
|INTEGER|JDBC**整数**型は符号付き 32 ビット整数を表します。 これはマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **int**型です。|  
|bigint|JDBC **BIGINT**型は符号付き 64 ビット整数を表します。 これはマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **bigint**型です。|  
|NUMERIC|JDBC**数値**型同一有効桁数の値を保持する固定長の有効桁数の 10 進値を表します。 **数値**型にマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **数値**型です。|  
|[DECIMAL]|JDBC **DECIMAL**型指定された有効桁数を少なくともの値を保持固定有効桁数の 10 進値を表します。 **DECIMAL**型にマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **decimal**型です。<br /><br /> JDBC **DECIMAL**型にもマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **money**と**smallmoney** 8 および 4 に格納されている特定の固定有効桁数の decimal 型である型バイト、それぞれします。|  
  
## <a name="approximate-numeric-types"></a>概数型  
 JDBC の概数型は**実際**、**二重**、および**FLOAT**です。  
  
|型|Description|  
|----------|-----------------|  
|REAL|JDBC**実際**型 7 桁の有効桁数 (有効桁数は 1 つ) があり、マップに直接、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **実際**型です。|  
|DOUBLE|JDBC**二重**型 15 桁 (倍精度) があり、マップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **float**型です。 JDBC **FLOAT**型は、シノニムの**二重**です。 混同できるので**FLOAT**と**二重**、**二重**をお勧めします。|  
  
## <a name="datetime-types"></a>Datetime 型  
 JDBC**タイムスタンプ**型にマップ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime**と**smalldatetime**型です。 **Datetime**型は、2 つの 4 バイト整数に格納します。 **Smalldatetime**型 (日付と時刻) は、同じ情報を保持する精度が低く、次の 2 つの 2 バイトの小さい整数にします。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]**タイムスタンプ**型は固定長バイナリ文字列型です。 JDBC の時刻型のいずれかにもマップされない:**日付**、**時間**、または**タイムスタンプ**です。  
  
## <a name="custom-type-mapping"></a>カスタム型のマッピング  
 SQLData インターフェイスを使用して、JDBC の JDBC のカスタム型マッピングの機能には、型 (Udt、Struct など) が高度な。 JDBC driver では実装されていません。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  

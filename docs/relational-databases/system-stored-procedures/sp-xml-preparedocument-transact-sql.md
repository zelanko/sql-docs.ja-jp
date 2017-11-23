---
title: "sp_xml_preparedocument (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_xml_preparedocument_TSQL
- sp_xml_preparedocument
dev_langs: TSQL
helpviewer_keywords: sp_xml_preparedocument
ms.assetid: 95f41cff-c52a-4182-8ac6-bf49369d214c
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de3ff49a53061f7a804c44886535f764e445fb2e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spxmlpreparedocument-transact-sql"></a>sp_xml_preparedocument (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  入力値として提供された XML テキストを読み取り、MSXML パーサー (Msxmlsql.dll) を使用して解析し、使用できる状態の解析済みドキュメントを提供します。 この解析済みのドキュメントでは、XML ドキュメント内の各種ノード (要素、属性、テキスト、コメントなど) がツリー形式で表示されます。  
  
 **sp_xml_preparedocument** XML ドキュメントの新しく作成された内部表現へのアクセスに使用できるハンドルを返します。 このハンドルは、期間中または実行することによって、ハンドルが無効にするまで、セッションの有効な**sp_xml_removedocument**です。  
  
> [!NOTE]  
>  解析済みドキュメントがの内部キャッシュに格納されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 MSXML パーサーの 8 分の 1 つ、合計使用可能なメモリを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 メモリ不足を回避するには、実行**sp_xml_removedocument**メモリを解放します。  
  
> [!NOTE]  
>  旧バージョンと互換性のため、 **sp_xml_preparedocument**折りたたみます CR (char(13)) と LF (これらの文字はエンティティに変換する場合でも属性で char(10)) 文字です。  
  
> [!NOTE]  
>  によって呼び出された XML パーサー **sp_xml_preparedocument**内部 Dtd およびエンティティ宣言を解析できます。 悪意を持って作成された Dtd およびエンティティのため、サービス拒否攻撃を実行する宣言を使用できる、ユーザーは、信頼されていないソースから XML ドキュメントを直接渡すを強くお勧め**sp_xml_preparedocument**です。  
>   
>  再帰的なエンティティ拡張攻撃を軽減するために**sp_xml_preparedocument**ドキュメントの最上位レベルに 1 つのエンティティの下に展開できるエンティティの数を 10,000 に制限します。 この制限は、文字エンティティまたは数値エンティティには適用されません。 この制限により、多数のエンティティ参照があるドキュメントを格納できるようになりますが、エンティティを再帰的に展開して、単一のエンティティで 10,000 個の展開より長いチェーンにすることはできなくなります。  
  
> [!NOTE]  
>  **sp_xml_preparedocument** 256 に同時に開くことができる要素の数を制限します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_xml_preparedocument  
hdoc   
OUTPUT  
[ , xmltext ]  
[ , xpath_namespaces ]   
```  
  
## <a name="arguments"></a>引数  
 *hdoc*  
 新しく作成されたドキュメントへのハンドルを指定します。 *hdoc*整数です。  
  
 [ *xmltext* ]  
 元の XML ドキュメントを指定します。 MSXML パーサーではこの XML ドキュメントが解析されます。 *xmltext*テキスト パラメーターです: **char**、 **nchar**、 **varchar**、 **nvarchar**、**テキスト**、 **ntext**または**xml**です。 既定値は NULL です。NULL の場合、空の XML ドキュメントの内部表現が作成されます。  
  
> [!NOTE]  
>  **sp_xml_preparedocument**テキストまたは型指定されていない XML だけを処理できます。 入力値として使用するインスタンス値が既に型指定された XML である場合は、まずその値を、型指定されない新しい XML インスタンスまたは文字列にキャストし、その後入力値として渡します。 詳細については、「 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)」を参照してください。  
  
 [ *xpath_namespaces* ]  
 OPENXML の XPath 式の行および列で使用される名前空間宣言を指定します。 *xpath_namespaces*テキスト パラメーターです: **char**、 **nchar**、 **varchar**、 **nvarchar**、**テキスト**、 **ntext**または**xml**です。  
  
 既定値は **\<root xmlns:mp ="urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}--microsoft-com:xml-metaprop">**です。 *xpath_namespaces*整形式 XML ドキュメントを使用して OPENXML の XPath 式で使用されるプレフィックスに対する名前空間 Uri を提供します。 *xpath_namespaces*名前空間を参照するために使用する必要がありますプレフィックスを宣言します**urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}--microsoft-com:xml-metaprop**; これが解析された XML 要素に関するメタデータを提供します。 この方法を使用して、メタプロパティ名前空間に対する名前空間プレフィックスを再定義できますが、再定義してもこの名前空間が失われることはありません。 プレフィックス**mp**は現在も有効**urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}--microsoft-com:xml-metaprop**場合でも*xpath_namespaces*このような宣言が含まれていません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-preparing-an-internal-representation-for-a-well-formed-xml-document"></a>A. ウェルフォームド XML ドキュメントの内部表現を準備する  
 次の例では、入力値として提供されている、新しく作成された XML ドキュメントの内部表現へのハンドルを返します。 `sp_xml_preparedocument` の呼び出しでは、既定の名前空間プレフィックス マッピングを使用します。  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
-- Remove the internal representation.  
exec sp_xml_removedocument @hdoc;  
```  
  
### <a name="b-preparing-an-internal-representation-for-a-well-formed-xml-document-with-a-dtd"></a>B. ウェルフォームド XML ドキュメントの内部表現を DTD を使用して準備する  
 次の例では、入力値として提供されている、新しく作成された XML ドキュメントの内部表現へのハンドルを返します。 このストアド プロシージャでは、読み込まれたドキュメントが、ドキュメント内に含まれる DTD に対して検証されます。 `sp_xml_preparedocument` の呼び出しでは、既定の名前空間プレフィックス マッピングを使用します。  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(2000);  
SET @doc = '  
<?xml version="1.0" encoding="UTF-8" ?>   
<!DOCTYPE root   
[<!ELEMENT root (Customers)*>  
<!ELEMENT Customers EMPTY>  
<!ATTLIST Customers CustomerID CDATA #IMPLIED ContactName CDATA #IMPLIED>]>  
<root>  
<Customers CustomerID="ALFKI" ContactName="Maria Anders"/>  
</root>';  
  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
```  
  
### <a name="c-specifying-a-namespace-uri"></a>C. 名前空間 URI を指定する  
 次の例では、入力値として提供されている、新しく作成された XML ドキュメントの内部表現へのハンドルを返します。 呼び出し`sp_xml_preparedocument`保持、`mp`メタプロパティ名前空間マッピング プレフィックスが強化され、`xyz`名前空間マッピング プレフィックス`urn:MyNamespace`です。  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc, '<ROOT xmlns:xyz="urn:MyNamespace"/>';  
```  
  
## <a name="see-also"></a>参照  
 [XML ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_xml_removedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)   
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)  
  
  

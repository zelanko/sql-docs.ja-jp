---
title: "xml_schema_namespace (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_schema_namespace_TSQL
- xml_schema_namespace
dev_langs:
- TSQL
helpviewer_keywords:
- XML schema collections [SQL Server], reconstructing schemas
- xml_schema_namespace function
- reconstructing schemas
- schemas [SQL Server], XML
- schema collections [SQL Server], reconstructing schemas
ms.assetid: ee9873d8-dd3a-4bff-a10c-68bbadbdf1a6
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 449e545672192baa9d16204afe1fb23497959094
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="xmlschemanamespace"></a>xml_schema_namespace
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された XML スキーマ コレクション内のすべてのスキーマまたは特定のスキーマを再構築します。 この関数は、 **xml** データ型のインスタンスを返します。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```  
  
xml_schema_namespace( Relational_schema , XML_schema_collection_name , [ Namespace ] )  
```  
  
## <a name="arguments"></a>引数  
 *Relational_schema*  
 リレーショナル スキーマの名前です。 *Relational_schema*は**sysname**です。  
  
 *XML_schema_collection_name*  
 再構築する XML スキーマ コレクションの名前を指定します。 *XML_schema_collection_name*は**sysname**です。  
  
 *名前空間*  
 再構築する XML スキーマの名前空間 URI を指定します。 上限は 1,000 文字です。 名前空間 URI を指定しない場合、XML スキーマ コレクション全体が再構築されます。 *Namespace*は**nvarchar (4000)**です。  
  
## <a name="return-types"></a>戻り値の型  
 **xml**  
  
## <a name="remarks"></a>解説  
 使用して、データベース内の XML スキーマ コンポーネントをインポートすると[CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)または[ALTER XML SCHEMA COLLECTION](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md)検証のために使用されるスキーマの情報が保持されます。 したがって、再構築されたスキーマは、元のスキーマ ドキュメントとは構文的に同じにならない可能性があります。 特に、コメント、空白、および注釈は失われ、暗黙的な型の情報が明示されます。 たとえば、 \<xs:element name ="e1"/> になります\<xs:element name ="e1"type ="xs:anyType"/>。 また、名前空間プレフィックスは保持されません。  
  
 名前空間のパラメーターを指定した場合、結果のスキーマ ドキュメントにはその名前空間内のすべてのスキーマ コンポーネントの定義が含まれます。それらのコンポーネントが異なるスキーマ ドキュメントまたは DDL のステップ、あるいはその両方に追加された場合であっても、同様です。  
  
 XML スキーマ ドキュメントを構築するために、この関数を使用することはできません、 **sys.sys** XML スキーマ コレクションです。  
  
## <a name="examples"></a>使用例  
 次の例は、XML スキーマ コレクションを取得`ProductDescriptionSchemaCollection`、実稼働リレーショナル スキーマから、`AdventureWorks2012`データベース。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT xml_schema_namespace(N'production',N'ProductDescriptionSchemaCollection');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [格納されている XML スキーマ コレクションの表示](../../relational-databases/xml/view-a-stored-xml-schema-collection.md)   
 [XML スキーマ コレクション &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  


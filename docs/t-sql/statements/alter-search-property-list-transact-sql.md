---
title: "ALTER SEARCH PROPERTY LIST (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SEARCH_PROPERTY_TSQL
- ALTER_SEARCH_PROPERTY_LIST_TSQL
- ALTER SEARCH PROPERTY LIST
- ALTER SEARCH PROPERTY
- ALTER_SEARCH_TSQL
- ALTER SEARCH
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], altering
- ALTER SEARCH PROPERTY LIST statement
ms.assetid: 0436e4a8-ca26-4d23-93f1-e31e2a1c8bfb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b56d1ae0be7a8aaef93011d6ecfde378a3e8fe91
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-search-property-list-transact-sql"></a>ALTER SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  指定した検索プロパティを、指定した検索プロパティ リストに追加します。または、指定した検索プロパティを、指定した検索プロパティ リストから削除します。  
  
## <a name="syntax"></a>構文  
  
```  
ALTER SEARCH PROPERTY LIST list_name  
{  
   ADD 'property_name'  
     WITH   
      (   
          PROPERTY_SET_GUID = 'property_set_guid'  
        , PROPERTY_INT_ID = property_int_id  
      [ , PROPERTY_DESCRIPTION = 'property_description' ]  
      )  
 | DROP 'property_name'   
}  
;  
```  
  
## <a name="arguments"></a>引数  
 *list_name*  
 変更するプロパティ リストの名前を指定します。 *list_name*識別子です。  
  
 表示するには既存のプロパティ リストの名前を使用して、 [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)カタログ ビューを次のようにします。  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
 ADD  
 指定したプロパティ リストに指定した検索プロパティを追加*list_name*です。 プロパティが、検索プロパティ リストに登録されます。 新しく追加されたプロパティをプロパティ検索で使用できるようにするには、関連付けられたフルテキスト インデックスを再作成する必要があります。 詳細については、「 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)」を参照してください。  
  
> [!NOTE]  
>  検索プロパティ リストに特定の検索プロパティを追加するには、そのプロパティ セット GUID を指定する必要があります (*property_set_guid*) およびプロパティ整数 ID (*property_int_id 句*)。 詳細については、このトピックの「プロパティ値の取得」を参照してください。  
  
 *property_name*  
 フルテキスト クエリでプロパティを識別するために使用される名前を指定します。 *property_name*プロパティ セット内のプロパティを一意に識別する必要があります。 プロパティ名の内部にはスペースを含めることができます。 最大長*property_name* 256 文字です。 この名前は、作成者や自宅の住所などのわかりやすい名前またはことができます、プロパティの Windows の正規名など**System.Author**または**System.Contact.HomeAddress**です。  
  
 開発者が指定した値を使用する必要があります*property_name* 、プロパティを識別、 [CONTAINS](../../t-sql/queries/contains-transact-sql.md)述語。 そのため、設定すると、指定されたプロパティによって定義されたプロパティを明確に表す値を指定することが重要プロパティを追加する GUID (*property_set_guid*) とプロパティの識別子 (*property_int_id*)。 プロパティ名の詳細については、このトピックの「解説」を参照してください。  
  
 現在のデータベースの検索プロパティ リストに現在存在するプロパティの名前を表示する、 [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)カタログ ビューを次のようにします。  
  
```  
SELECT property_name FROM sys.registered_search_properties;  
```  
  
 PROPERTY_SET_GUID ='*property_set_guid*'  
 プロパティが属するプロパティ セットの識別子を指定します。 これはグローバル一意識別子 (GUID) です。 この値の取得に関する情報については、このトピックの「解説」を参照してください。  
  
 プロパティを表示するには、使用して、現在のデータベースの検索プロパティ リストに存在するプロパティの GUID を設定、 [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)カタログ ビューを次のようにします。  
  
```  
SELECT property_set_guid FROM sys.registered_search_properties;  
```  
  
 Property_int_id 句 =*property_int_id 句*  
 プロパティ セット内のプロパティを識別する整数を指定します。 この値の取得に関する情報については、「解説」を参照してください。  
  
 現在のデータベースの検索プロパティ リストに存在する任意のプロパティ整数識別子を表示するには、使用、 [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)カタログ ビューを次のようにします。  
  
```  
SELECT property_int_id FROM sys.registered_search_properties;  
```  
  
> [!NOTE]  
>  特定の組み合わせ*property_set_guid*と*property_int_id 句*検索プロパティ リスト内で一意である必要があります。 既存の組み合わせを追加しようとすると、ALTER SEARCH PROPERTY LIST 操作が失敗しエラーが発生します。 つまり、1 つのプロパティに定義できる名前は 1 つだけです。  
  
 PROPERTY_DESCRIPTION ='*property_description*'  
 プロパティに関するユーザー定義の説明を指定します。 *property_description*最大 512 文字の文字列を指定します。 このオプションは省略可能です。  
  
 DROP  
 指定したプロパティ リストから削除プロパティで指定された*list_name*です。 プロパティを削除すると登録が解除されるため、このプロパティは検索できなくなります。  
  
## <a name="remarks"></a>解説  
 それぞれのフルテキスト インデックスは、検索プロパティ リストを 1 つだけ持つことができます。  
  
 特定の検索プロパティのクエリを有効にするには、フルテキスト インデックスの検索プロパティ リストにその検索プロパティを追加した後、インデックスの再作成を行う必要があります。  
  
 プロパティを指定する場合は、PROPERTY_SET_GUID 句、PROPERTY_INT_ID 句、および PROPERTY_DESCRIPTION 句を、かっこで囲まれたコンマ区切りのリストとして任意の順序で指定できます。次に例を示します。  
  
```  
ALTER SEARCH PROPERTY LIST CVitaProperties  
ADD 'System.Author'   
WITH (   
      PROPERTY_DESCRIPTION = 'Author or authors of a given document.',  
      PROPERTY_SET_GUID   = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',   
      PROPERTY_INT_ID = 4   
      );  
```  
  
> [!NOTE]  
>  この例では、Windows Vista で導入された正規プロパティ名 (Windows の正規名) の概念に似ているプロパティ名 `System.Author` を使用しています。  
  
## <a name="obtaining-property-values"></a>プロパティ値の取得  
 フルテキスト検索では、プロパティ セット GUID とプロパティ整数 ID を使用して、検索プロパティがフルテキスト インデックスにマップされます。 Microsoft によって定義されているプロパティのこれらを取得する方法については、次を参照してください。 [Find Property Set GUIDs および検索プロパティのプロパティ整数 Id](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)です。 独立系ソフトウェア ベンダー (ISV) によって定義されたプロパティの詳細については、そのベンダーのマニュアルを参照してください。  
  
## <a name="making-added-properties-searchable"></a>追加したプロパティを検索可能にする  
 検索プロパティを検索プロパティ リストに追加すると、そのプロパティが登録されます。 新しく追加されたプロパティをすぐに指定することができます[CONTAINS](../../t-sql/queries/contains-transact-sql.md)クエリ。 ただし、関連付けられているフルテキスト インデックスを再作成しない限り、新しく追加されたプロパティに対するプロパティスコープのフルテキスト クエリを実行してもドキュメントは返されません。 たとえば、次プロパティ スコープのクエリ、新しく追加されたプロパティを*new_search_property*、対象のテーブルに関連付けられているフルテキスト インデックスまでのすべてのドキュメントは返されません (*table_name*) が再作成します。  
  
```  
SELECT column_name  
FROM table_name  
WHERE CONTAINS( PROPERTY( column_name, 'new_search_property' ), 
               'contains_search_condition');  
GO   
```  
  
 完全作成を開始するには、次を使用[ALTER FULLTEXT INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-fulltext-index-transact-sql.md)ステートメント。  
  
```  
USE database_name;  
GO  
ALTER FULLTEXT INDEX ON table_name START FULL POPULATION;  
GO  
```  
  
> [!NOTE]  
>  プロパティ リストからプロパティを削除した場合、検索プロパティ リストに残っているプロパティのみがフルテキスト クエリの対象となるため、インデックスを再作成する必要はありません。  
  
## <a name="related-references"></a>関連リファレンス  
 **プロパティ リストを作成するには**  
  
-   [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)  
  
 **プロパティ リストを削除するには**  
  
-   [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)  
  
 **追加またはフルテキスト インデックスのプロパティ リストを削除するには**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
 **フルテキスト インデックスのカタログの作成を実行するには**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> アクセス許可  
 プロパティ リストに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-adding-a-property"></a>A. プロパティを追加する  
 次の例では、いくつかのプロパティ (`Title`、`Author`、`Tags` など) を、`DocumentPropertyList` という名前のプロパティ リストに追加します。  
  
> [!NOTE]  
>  作成する例については`DocumentPropertyList`プロパティ リストを参照してください[CREATE SEARCH PROPERTY LIST &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
   ADD 'Title'   
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Author'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 4,   
      PROPERTY_DESCRIPTION = 'System.Author - Author or authors of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Tags'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 5,   
      PROPERTY_DESCRIPTION = 
          'System.Keywords - Set of keywords (also known as tags) assigned to the item.' );  
```  
  
> [!NOTE]  
>  プロパティスコープのクエリで使用する前に、特定の検索プロパティ リストをフルテキスト インデックスに関連付ける必要があります。 これを行うを使用して、 [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md)ステートメント SET SEARCH PROPERTY LIST 句を指定するとします。  
  
### <a name="b-dropping-a-property"></a>B. プロパティを削除する  
 次の例では、`Comments` プロパティを `DocumentPropertyList` プロパティ リストから削除します。  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
DROP 'Comments' ;  
```  
  
## <a name="see-also"></a>参照  
 [SEARCH PROPERTY LIST &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [DROP SEARCH PROPERTY LIST &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-search-property-list-transact-sql.md)   
 [sys.registered_search_properties &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.dm_fts_index_keywords_by_property &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [検索プロパティのプロパティ セット GUID およびプロパティ整数 ID の取得](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
  

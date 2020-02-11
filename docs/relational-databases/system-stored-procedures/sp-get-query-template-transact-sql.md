---
title: sp_get_query_template (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_get_query_template
- sp_get_query_template_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_get_query_template
ms.assetid: 85e9bef7-2417-41a8-befa-fe75507d9bf2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9841e7815f31af26aeeb3ed0f4783d3a36d83030
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124082"
---
# <a name="sp_get_query_template-transact-sql"></a>sp_get_query_template (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パラメーター化された形式のクエリを返します。 返される結果は、強制パラメーター化の使用によるパラメーター化形式のクエリに似ています。 sp_get_query_template は、主にテンプレートプランガイドを作成するときに使用されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_get_query_template  
   [ @querytext = ] N'query_text'  
   , @templatetext OUTPUT   
   , @parameters OUTPUT   
```  
  
## <a name="arguments"></a>引数  
 '*query_text*'  
 パラメーター化されたバージョンを生成するクエリを指定します。 '*query_text*' は、単一引用符で囲む必要があります。また、前には N Unicode 指定子を指定する必要があります。 N '*query_text*' は、 @querytextパラメーターに割り当てられた値です。 **Nvarchar (max)** 型です。  
  
 @templatetext  
 パラメーター化された形式の*query_text*を文字列リテラルとして受け取る、 **nvarchar (max)** 型の出力パラメーターを指定します。  
  
 @parameters  
 は、に@templatetextよってパラメーター化されたパラメーター名とデータ型の文字列リテラルを受け取る、 **nvarchar (max)** 型の出力パラメーターです。  
  
## <a name="remarks"></a>解説  
 sp_get_query_template は、以下のことが発生した場合にエラーを返します。  
  
-   *Query_text*の定数リテラル値をパラメーター化しません。  
  
-   *query_text*が NULL であるか、Unicode 文字列ではないか、構文が正しくないか、またはコンパイルできません。  
  
 Sp_get_query_template がエラーを返す場合、 @templatetextと@parametersの出力パラメーターの値は変更されません。  
  
## <a name="permissions"></a>アクセス許可  
 public データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、2 つの定数リテラル値が含まれたパラメーター化形式のクエリが返されます。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @my_templatetext nvarchar(max)  
DECLARE @my_parameters nvarchar(max)  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
        FROM Production.ProductModel pm   
        INNER JOIN Production.ProductInventory pi  
        ON pm.ProductModelID = pi.ProductID  
        WHERE pi.ProductID = 2  
        GROUP BY pi.ProductID, pi.Quantity  
        HAVING SUM(pi.Quantity) > 400',  
@my_templatetext OUTPUT,  
@my_parameters OUTPUT;  
SELECT @my_templatetext;  
SELECT @my_parameters;  
```  
  
 `@my_templatetext``OUTPUT`パラメーターのパラメーター化された結果を次に示します。  
  
 `select pi . ProductID , SUM ( pi . Quantity ) as Total`  
  
 `from Production . ProductModel pm`  
  
 `inner join Production . ProductInventory pi`  
  
 `on pm . ProductModelID = pi . ProductID`  
  
 `where pi . ProductID = @0`  
  
 `group by pi . ProductID , pi . Quantity`  
  
 `having SUM ( pi . Quantity ) > 400`  
  
 最初の定数リテラル`2`のは、パラメーターに変換されることに注意してください。 2 番目のリテラル `400` は `HAVING` 句の内部にあるため、変換されません。 sp_get_query_template によって返される結果は、ALTER DATABASE の PARAMETERIZATION オプションが FORCED に設定されている場合のパラメーター化形式クエリに似ています。  
  
 `@my_parameters OUTPUT`パラメーターのパラメーター化された結果を次に示します。  
  
```  
@0 int  
```  
  
> [!NOTE]  
>  sp_get_query_template の出力内のパラメーターの順序と名前は、Quick Fix Engineering、Service Pack、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンのアップグレードによって変化する可能性があります。 また、アップグレードによって、同じクエリに対して異なる定数リテラルのセットがパラメーター化され、両方の出力パラメーターの結果に適用される間隔が異なる場合もあります。  
  
## <a name="see-also"></a>参照  
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [プラン ガイドを使用したクエリのパラメーター化動作の指定](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)  
  
  

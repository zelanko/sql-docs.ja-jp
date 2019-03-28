---
title: sp_OAMethod (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAMethod
- sp_OAMethod_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAMethod
ms.assetid: 1dfaebe2-c7cf-4041-a586-5d04faf2e25e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 703b6464d035d06583193aedaa330257fc38fe34
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530374"
---
# <a name="spoamethod-transact-sql"></a>sp_OAMethod (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  OLE オブジェクトのメソッドを呼び出します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_OAMethod objecttoken , methodname  
    [ , returnvalue OUTPUT ]   
    [ , [ @parametername = ] parameter [ OUTPUT ] [ ...n ] ]   
```  
  
## <a name="arguments"></a>引数  
 *objecttoken*  
 使用して作成した OLE オブジェクトのオブジェクト トークン**sp_OACreate**します。  
  
 *Methodname*  
 呼び出す OLE オブジェクトのメソッド名です。  
  
 _returnvalue_  **OUTPUT**  
 OLE オブジェクトのメソッドの戻り値です。 指定する場合は、適切なデータ型のローカル変数でなければなりません。  
  
 ローカル変数を指定するいずれかのメソッドが 1 つの値を返す場合*returnvalue*、ローカル変数の値を返すかを指定しないメソッドを返す*returnvalue*、返された、メソッドは、単一列、単一行の結果セットとしてクライアントに値を返します。  
  
 メソッドの戻り値が OLE オブジェクト場合*returnvalue*データ型のローカル変数にする必要があります**int**します。オブジェクト トークンが、ローカル変数に格納されているし、その他の OLE オートメーション ストアド プロシージャでは、このオブジェクト トークンを使用できます。  
  
 メソッドの戻り値が配列では場合、 *returnvalue*を指定すると、NULL に設定されます。  
  
 次のいずれかが発生した場合、エラーが発生します。  
  
-   *returnvalue*が指定されているが、メソッドが値を返しません。  
  
-   メソッドは、2 つ以上の次元の配列を返します。  
  
-   メソッドが出力パラメーターとして配列を返す場合  
  
`[ _@parametername = ] parameter[ OUTPUT ]` メソッドのパラメーターです。 指定した場合*パラメーター*適切なデータ型の値を指定する必要があります。  
  
 出力パラメーターの戻り値を取得する*パラメーター*適切なデータ型のローカル変数にする必要がありますと**出力**指定する必要があります。 定数パラメーターが指定されている場合、または場合**出力**が指定されていない、戻り値出力パラメーターからは無視されます。  
  
 指定した場合*parametername*の名前を指定する必要があります、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]名前付きパラメーター。 なお**@**_parametername_is されません、[!INCLUDE[tsql](../../includes/tsql-md.md)]ローカル変数。 アット マーク (**@**) が削除されると*parametername*パラメーター名として OLE オブジェクトに渡されます。 すべての位置指定パラメーターを指定した後、すべての名前付きパラメーターを指定する必要があります。  
  
 *n*  
 複数のパラメーターを指定できることを示すプレース ホルダーです。  
  
> [!NOTE]
>  *@parametername* 指定したメソッドの一部であり、オブジェクトに渡されますために、名前付きパラメーターを指定できます。 このストアド プロシージャの他のパラメーターは、名前ではなく位置で指定されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または OLE オートメーション オブジェクトによって返される HRESULT の整数値である 0 以外の値の数 (失敗)。  
  
 HRESULT のリターン コードの詳細については[OLE オートメーションのリターン コードとエラー情報](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md)します。  
  
## <a name="result-sets"></a>結果セット  
 メソッドの戻り値が 1 次元または 2 次元の配列である場合、配列は結果セットとしてクライアントに返されます。  
  
-   1 次元の配列の場合は、配列内の要素数と同数の列を持つ 1 行の結果セットとしてクライアントに返されます。 つまり、配列は (列数) として返されます。  
  
-   2 次元の配列の場合は、最初の次元の配列の要素数を列数とし、2 番目の次元の配列の要素数を行数とした結果セットとしてクライアントに返します。 つまり、(列、行) として、配列が返されます。  
  
 ときに、プロパティの戻り値またはメソッドの戻り値は、配列**sp_OAGetProperty**または**sp_OAMethod**クライアントに結果セットを返します。 メソッドの出力パラメーターを配列にすることはできません。これらのプロシージャは、配列内のすべてのデータ値をスキャンし、結果セットのそれぞれの列に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の適切なデータ型とデータ長を決定します。 これらのプロシージャは必要なデータ型とデータ長を使用して、特定の列内のすべてのデータ値を表現します。  
  
 列内のすべてのデータ値が同じデータ型を共有する場合は、そのデータ型を列全体で使用します。 列のデータ値は、異なるデータ型が場合、は、次の表に基づいて列全体のデータ型が選択します。  
  
||ssNoversion|FLOAT|money|DATETIME|varchar|NVARCHAR|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>コメント  
 使用することも**sp_OAMethod**プロパティ値を取得します。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calling-a-method"></a>A. メソッドを呼び出す  
 次の例では、`Connect`メソッドの前に作成**SQLServer**オブジェクト。  
  
```  
EXEC @hr = sp_OAMethod @object, 'Connect', NULL, 'my_server',  
    'my_login', 'my_password';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
### <a name="b-getting-a-property"></a>B. プロパティを取得します。  
 次の例では、取得、`HostName`プロパティ (の前に作成**SQLServer**オブジェクト)、ローカル変数に格納します。  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAMethod @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
PRINT @property;  
```  
  
## <a name="see-also"></a>参照  
 [OLE オートメーション ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE オートメーションのサンプル スクリプト](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  

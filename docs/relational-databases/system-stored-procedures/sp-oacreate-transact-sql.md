---
title: sp_OACreate (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_OACreate
- sp_OACreate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OACreate
ms.assetid: eb84c0f1-26dd-48f9-9368-13ee4a30a27c
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2c7f4598f309549a34cc9dbc39b0ba1a964160bc
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spoacreate-transact-sql"></a>sp_OACreate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  OLE オブジェクトのインスタンスを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_OACreate { progid | clsid } , objecttoken OUTPUT [ , context ]   
```  
  
## <a name="arguments"></a>引数  
 *progid*  
 作成する OLE オブジェクトのプログラム ID (ProgID) を指定します。 この文字の文字列が OLE オブジェクトのクラスについて説明しは、形式があります: **'***OLEComponent***.***オブジェクト***'**  
  
 *OLEComponent* OLE オートメーション サーバーのコンポーネント名と*オブジェクト*OLE オブジェクトの名前を指定します。 指定した OLE オブジェクトが有効にする必要があり、サポートする必要があります、 **IDispatch**インターフェイスです。  
  
 たとえば、SQLDMO です。Sql Server は、SQL-DMO の ProgID **SQLServer**オブジェクト。 SQL-DMO は SQLDMO のコンポーネント名を持ち、 **SQLServer**オブジェクトが有効であり、(すべての SQL-DMO のようなオブジェクト)、 **SQLServer**オブジェクトのサポート**IDispatch**です。  
  
 *clsid*  
 作成する OLE オブジェクトのクラス ID (CLSID) を指定します。 この文字の文字列が OLE オブジェクトのクラスについて説明しは、形式があります: **' {***nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn***}'** です。 指定した OLE オブジェクトが有効にする必要があり、サポートする必要があります、 **IDispatch**インターフェイスです。  
  
 たとえば、SQL-DMO の CLSID は、{00026BA1-0000-0000-C000-000000000046} **SQLServer**オブジェクト。  
  
 *objecttoken* **出力**  
 返されるオブジェクト トークンは、データ型のローカル変数でなければなりません**int**です。このオブジェクト トークンは、作成する OLE オブジェクトを識別するもので、その他の OLE オートメーション ストアド プロシージャの呼び出しに使用されます。  
  
 *context*  
 新しく作成した OLE オブジェクトを実行するときの実行条件を指定します。 指定する場合は、次のいずれかの値を指定する必要があります。  
  
 **1** = 組み込み (.dll) OLE サーバーのみです。  
  
 **4** = ローカル (.exe) OLE サーバーのみです。  
  
 **5**許可されるインプロセスおよびローカル OLE サーバーを =  
  
 指定されていない場合、既定値は**5**です。 この値は、 *dwClsContext*への呼び出しのパラメーター **CoCreateInstance**です。  
  
 インプロセス OLE サーバーが許可された場合 (のコンテキスト値を使用して**1**または**5**またはされたコンテキストの値が指定されない) メモリへのアクセス権を持つ、およびその他のリソースを所有[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 組み込み OLE サーバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリやリソースに損傷を与え、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアクセス違反など予期しない結果を招く場合があります。  
  
 コンテキストの値を指定すると**4**、ローカル OLE サーバーでは、いずれかにアクセスできない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リソース、およびそれが破損することはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリまたはリソースします。  
  
> [!NOTE]  
>  このストアド プロシージャのパラメーターは、名前ではなく位置で指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0、失敗した場合は OLE オートメーション オブジェクトによって返される HRESULT の 0 以外の整数値を返します。  
  
 HRESULT のリターン コードの詳細については、次を参照してください。 [OLE オートメーションのリターン コードとエラー情報](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md)です。  
  
## <a name="remarks"></a>解説  
 OLE オートメーション プロシージャが有効な場合に呼び出し**sp_OACreate** OLE オートメーションの共有実行環境を開始します。 OLE オートメーションを有効にする方法の詳細については、次を参照してください。 [Ole Automation Procedures サーバー構成オプション](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)です。  
  
 作成された OLE オブジェクトは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント バッチの最後に自動的に破棄されます。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-progid"></a>A. ProgID を使用する  
 次の例は、SQL-DMO **SQLServer**オブジェクトの ProgID を使用しています。  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate 'SQLDMO.SQLServer', @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
### <a name="b-using-clsid"></a>B. CLSID を使用する  
 次の例は、SQL-DMO **SQLServer**オブジェクトの CLSID を使用しています。  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate '{00026BA1-0000-0000-C000-000000000046}',  
    @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [OLE オートメーション ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Ole Automation Procedures サーバー構成オプション](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)   
 [OLE オートメーションのサンプル スクリプト](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  

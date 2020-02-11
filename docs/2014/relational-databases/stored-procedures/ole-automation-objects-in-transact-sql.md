---
title: Transact-SQL での OLE オートメーション オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 06913c27af89657aef5a0a5397cd77a1ee025299
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211851"
---
# <a name="ole-automation-objects-in-transact-sql"></a>Transact-SQL での OLE オートメーション オブジェクト
  [!INCLUDE[tsql](../../includes/tsql-md.md)]には、バッチ、ストアドプロシージャ、およびトリガーで[!INCLUDE[tsql](../../includes/tsql-md.md)] OLE オートメーションオブジェクトを参照できるようにする、いくつかのシステムストアドプロシージャが含まれています。 これらのシステム ストアド プロシージャは拡張ストアド プロシージャとして動作します。また、これらのストアド プロシージャから実行される OLE オートメーション オブジェクトは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] アドレス空間の中で拡張ストアド プロシージャと同じように動作します。  
  
 OLE オートメーション ストアド プロシージャでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチから SQL DMO オブジェクトやカスタム OLE オートメーション オブジェクト ( **IDispatch** インターフェイスを公開しているオブジェクトなど) を参照できます。 
  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] を使用して作成するカスタム インプロセス OLE サーバーには、 **On Error GoTo** サブルーチンと **On Error GoTo** サブルーチン用に **On Error GoTo** ステートメントで指定されたエラー ハンドラーを実装する必要があります。 
  **Class_Initialize** サブルーチンと **Class_Terminate** サブルーチンで処理されないエラーが発生すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスでのアクセス違反など、予期しないエラーが発生する可能性があります。 また、その他のサブルーチン用のエラー ハンドラーも用意しておくことをお勧めします。  
  
 
  [!INCLUDE[tsql](../../includes/tsql-md.md)] で OLE オートメーション オブジェクトを使用する場合は、まず、**sp_OACreate** システム ストアド プロシージャを呼び出して、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスのアドレス空間にそのオブジェクトのインスタンスを作成します。  
  
 オブジェクトのインスタンスを作成した後、次のストアド プロシージャを呼び出してオブジェクトのプロパティ、メソッド、およびエラー情報を処理します。  
  
-   **sp_OAGetProperty**は、プロパティの値を取得します。  
  
-   プロパティの値を**sp_OASetProperty**設定します。  
  
-   **sp_OAMethod**はメソッドを呼び出します。  
  
-   **sp_OAGetErrorInfo**は、最新のエラー情報を取得します。  
  
 オブジェクトが必要なくなったら、 **sp_OADestroy** を呼び出し、 **sp_OACreate**で作成したオブジェクトのインスタンスの割り当てを解除します。  
  
 OLE オートメーション オブジェクトは、プロパティ値とメソッドを使用してデータを返します。 **sp_OAGetProperty**と**sp_OAMethod**は、これらのデータ値を結果セットの形式で返します。  
  
 OLE オートメーション オブジェクトのスコープはバッチです。 そのオブジェクトへのすべての参照は、単一のバッチ、ストアド プロシージャ、またはトリガー内に含まれている必要があります。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の OLE オートメーション オブジェクトからオブジェクトを参照する場合、参照するオブジェクトに含まれる他のオブジェクトも参照できます。 たとえば、SQL-DMO の **SQLServer** オブジェクトを使用すると、参照先のサーバーに含まれているデータベースとテーブルを参照できます。  
  
## <a name="related-content"></a>関連コンテンツ  
 [オブジェクト階層の構文 &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql)  
  
 [セキュリティ構成](../security/surface-area-configuration.md)  
  
 [Ole Automation Procedures サーバー構成オプション](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [sp_OACreate &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-oacreate-transact-sql)  
  
 [sp_OAGetProperty &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql)  
  
 [sp_OASetProperty &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql)  
  
 [sp_OAMethod &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-oamethod-transact-sql)  
  
 [sp_OAGetErrorInfo &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
 [sp_OADestroy &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-oadestroy-transact-sql)  
  
  

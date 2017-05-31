---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c5c47dd2a9d349da10e876f8da486790355be125
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver33081"></a>MSSQLSERVER_33081
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|33081|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|メッセージ テキスト|Authenticode 署名またはファイル パスが無効なため、暗号プロバイダー '%.*ls' を読み込めませんでした。  前のメッセージでその他のエラーを確認してください。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、エラー メッセージに表示されている暗号化サービス プロバイダーを読み込めませんでした。 このエラーの原因と考えられる Win API エラーがいくつかあります。 リング バッファーに、失敗した API の名前とその API によって返された Windows エラー コードが格納されています。 詳細情報を表示するには、次のクエリを使用して sys.dm_os_ring_buffers ビューにクエリを実行します。  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>ユーザーの操作  
問題を調査するには、MSDN (http://msdn.microsoft.com/) で Windows エラー コードを検索します。 エラーを解決するか、詳細について [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS に問い合わせます。 CSS へのお問い合わせの際には、次の情報を収集してサポート スタッフにご提供ください。  
  
-   暗号化サービス プロバイダーの読み込み失敗に関するエラーを示すエラー ログ。  
  
-   次のステートメントからの出力。  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
> リング バッファー情報は再起動時に失われる場合があるため、すばやく収集してください。  
  


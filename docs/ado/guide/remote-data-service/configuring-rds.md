---
description: RDS の構成
title: RDS の構成 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS configuration [ADO]
ms.assetid: 5dd48483-858a-48c2-98ce-f2359abe1f59
author: rothja
ms.author: jroth
ms.openlocfilehash: 23110157445da6c776de7582682992ab55a97ac8
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759880"
---
# <a name="configuring-rds"></a>RDS の構成
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 RDS を効率的に実装するには、使用できるさまざまな構成について理解している必要があります。 ここでは、RDS の実装におけるセキュリティとスケーラビリティに関する重要な情報について説明します。 RDS を使用するようにコンピューターを構成する方法については、次のトピックを参照してください。  
  
-   [Web サーバー コンピューターへのゲスト特権の付与](./granting-guest-privileges-to-a-web-server-computer.md)  
  
-   [カスタム ビジネス オブジェクトの登録](./registering-a-custom-business-object.md)  
  
-   [スクリプト用にビジネス オブジェクトを安全とマークする](./marking-business-objects-as-safe-for-scripting.md)  
  
-   [DCOM で使用するためにクライアントにビジネス オブジェクトを登録する](./registering-business-objects-on-the-client-for-use-with-dcom.md)  
  
-   [DCOM のストリームのマーシャリング形式の設定](./setting-dcom-stream-marshaling-format.md)  
  
-   [DCOM 上で実行するための DLL の有効化](./enabling-a-dll-to-run-on-dcom.md)  
  
-   [IIS での仮想サーバーの構成](./configuring-virtual-servers-on-iis.md)  
  
-   [RDS アプリケーションの保護](./securing-rds-applications.md)  
  
-   [安全または無制限モード用の DataFactory の構成](./configuring-datafactory-for-safe-or-unrestricted-modes.md)  
  
## <a name="see-also"></a>関連項目  
 [RDS での関連テクノロジの使用](./using-related-technologies-with-rds.md)   
 [DataFactory のカスタマイズ](./datafactory-customization.md)   
 [RDS のトラブルシューティング](./troubleshooting-rds.md)
---
title: カスタム ログ プロバイダー用ユーザー インターフェイスの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c60ec7f24dd5d6970697f112329e2d82b2e22af5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173991"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>カスタム ログ プロバイダー用ユーザー インターフェイスの開発
  多くの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ログ プロバイダーには、カスタム ユーザー インターフェイスがあります。カスタム ユーザー インターフェイスには <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> が実装され、**[SSIS ログの構成]** ダイアログ ボックスの **[構成]** ボックスが、使用可能な接続マネージャーがフィルター選択されたドロップダウン リストに置き換えられます。 ただし、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]では実装されていません。  
  
![Integration Services のアイコン (小)](../../media/dts-16.gif "Integration Services アイコン (小)")**Integration Services と終了日を維持** <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>参照  
 [カスタム ログ プロバイダーの作成](creating-a-custom-log-provider.md)   
 [カスタム ログ プロバイダーのコーディング](coding-a-custom-log-provider.md)  
  
  
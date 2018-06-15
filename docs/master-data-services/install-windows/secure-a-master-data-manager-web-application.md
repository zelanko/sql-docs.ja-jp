---
title: マスター データ マネージャー Web アプリケーションのセキュリティ保護 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 69007b20b70a8be2bbbca07fad46c51dee693ac7
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34323563"
---
# <a name="secure-a-master-data-manager-web-application"></a>マスター データ マネージャー Web アプリケーションのセキュリティ保護

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  HTTPS を使用して [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションをセキュリティ保護できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションは、HTTP または HTTPS のいずれかを使用できますが、両方を使用することはできません。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] がインストールされている Web サーバーの管理者である必要があります。  
  
-   MDS が Web サーバーにインストールされていて、Web アプリケーションが存在する必要があります。 詳細については、「 [マスター データ サービスのインストール](../../master-data-services/install-windows/install-master-data-services.md) 」および「 [マスター データ マネージャー Web アプリケーションの作成 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)」を参照してください。  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>HTTPS を使用してマスター データ マネージャー Web アプリケーションをセキュリティ保護するには  
  
1.  [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションが HTTP を使用して正しく構成されていることを確認した後、IIS で証明書を作成します。 詳細については、「 [IIS 7 でサーバー証明書を構成する](http://technet.microsoft.com/library/cc732230\(WS.10\).aspx)」を参照してください。  
  
2.  **[接続]** ペインの **[サイト]** で、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションをホストするサイトをクリックします。  
  
3.  **[アクション]** ペインで、 **[バインド]** をクリックします。  
  
4.  **[追加]** をクリックします。  
  
5.  一覧から、 **[https]** を選択します。  
  
6.  SSL 証明書を選択します。  
  
7.  **[OK]** をクリックします。  
  
8.  省略可。 HTTP を削除してユーザーが HTTPS のみを使用してサイトにアクセスできるようにするには、一覧の **[http]** の行をクリックします。 **[削除]** をクリックし、確認のダイアログ ボックスで **[はい]** をクリックします。  
  
    > [!IMPORTANT]  
    >  HTTP を削除した後に basicHttp 構成および wsHttpBinding 構成を変更する必要があります。  
  
9. **[サイト バインド]** ダイアログ ボックスを閉じるには、 **[閉じる]** をクリックします。  
  
10. ここで、 *ドライブ*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication にある web.config ファイルを開きます。  
  
11. " `<security mode="Message">` " という文字列を探して、" `<security mode="Transport">`" に変更します。  
  
12. ファイルを保存して閉じます。 エラーが発生した場合は、UAC が有効になっている可能性があります。 詳細については、 [ユーザー アカウント制御の無効化](http://technet.microsoft.com/library/cc709691\(WS.10\).aspx)に関する記事を参照してください。 これで、ユーザーが HTTPS を使用してサイトにアクセスできるようになりました。  
  
## <a name="see-also"></a>参照  
 [マスター データ マネージャー Web アプリケーションの作成 &#40;マスター データ サービス&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  

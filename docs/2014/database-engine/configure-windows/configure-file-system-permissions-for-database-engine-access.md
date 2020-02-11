---
title: データベース エンジン アクセスのファイル システム アクセス許可の構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b23ed3a3a1f128d24bfec2a0066e63b09753311a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62811326"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>データベース エンジン アクセスのファイル システム権限の構成
  このトピックでは [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]にデータベース ファイルの格納場所へのファイル システム アクセス権を付与する方法について説明します。 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスには、データベース ファイルが格納されているファイル フォルダーにアクセスするための Windows ファイル システム権限が必要です。 既定の場所への権限は、セットアップ中に構成されます。 別の場所にデータベース ファイルを配置した場合は、次の手順に従って、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] にその場所へのフル コントロール権限を付与する必要がある場合があります。  
  
 
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、権限は各サービスのサービスごとの SID に割り当てられます。 このシステムはサービスの分離と多層防御を提供するのに役立ちます。 サービスごとの SID はサービス名から取得され、各サービスに固有です。 トピック「 [Windows サービス アカウントと権限の構成](configure-windows-service-accounts-and-permissions.md) 」にはサービスごとの SID についての記載があり、「 **Windows の特権および権限**」で名前が指定されています。 サービスごとの SID に対して、ファイルの場所へのアクセス権を割り当てる必要があります。  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>サービスごとの SID にファイル システム権限を付与するには  
  
1.  エクスプローラーを使用して、データベース ファイルが格納されているファイル システムの場所に移動します。 ファイル システム フォルダーを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  
  **[セキュリティ]** タブで **[編集]** をクリックし、 **[追加]** をクリックします。  
  
3.  
  **[ユーザー、コンピューター、サービス アカウント、またはグループの選択]** ダイアログ ボックスで、場所の一覧の上部にある **[場所]** をクリックし、コンピューター名を選択して、 **[OK]** をクリックします。  
  
4.  **[選択するオブジェクト名を入力**してください] ボックスに、オンラインブックのトピック「 **Windows サービスアカウントと権限の構成**」に記載されているサービスごとの SID の名前を入力します。 (サービス[!INCLUDE[ssDE](../../includes/ssde-md.md)]ごとの SID については、既定のインスタンスの場合は**nt servicemssqlserver** 、名前付きインスタンスの場合は**Nt service\ MSSQL $ InstanceName**を使用します。)  
  
5.  
  **[名前の確認]** をクリックして、このエントリを検証します。 検証は多くの場合に失敗し、名前が見つからないことが示される場合があります。 
  **[OK]** をクリックすると、 **[複数の名前が見つかりました]** ダイアログ ボックスが表示されます。  
  
6.  ここで、サービスごとの SID ( **MSSQLSERVER**または**NT service\ MSSQL $ InstanceName**) を選択し、[ **OK]** をクリックします。  
  
7.  もう一度 [ **OK** ] をクリックして、[**アクセス許可**] ダイアログボックスに戻ります。  
  
8.  [**グループ名またはユーザー**名] ボックスで、サービスごとの SID を選択し、[>**の** \<アクセス許可] ボックスで、[**フルコントロール**] の [**許可**] チェックボックスをオンにします。  
  
9. 
  **[適用]** をクリックし、 **[OK]** を 2 回クリックして終了します。  
  
## <a name="see-also"></a>参照  
 [データベースエンジン Services を管理する](manage-the-database-engine-services.md)   
 [システムデータベースの移動](../../relational-databases/databases/system-databases.md)   
 [ユーザー データベースの移動](../../relational-databases/databases/move-user-databases.md)  
  
  

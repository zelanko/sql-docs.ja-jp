---
title: スナップショット ファイルの圧縮 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c8be85ae97d281113515205fadba9be827492474
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762572"
---
# <a name="compress-snapshot-files-sql-server-management-studio"></a>スナップショット ファイルの圧縮 (SQL Server Management Studio)
  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページでファイルを圧縮するように指定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。  
  
### <a name="to-compress-snapshot-files"></a>スナップショット ファイルを圧縮するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、以下の操作を実行します。  
  
    1.  **[ファイルを次のフォルダーに保存する]** チェック ボックスをオンにし、 **[参照]** をクリックしてディレクトリに移動するか、スナップショット ファイルの格納先ディレクトリへのパスを入力します。  
  
        > [!NOTE]  
        >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\snapshot など) で指定する必要があります。 詳細については、「[Secure the Snapshot Folder (スナップショット フォルダーのセキュリティ保護)](../security/secure-the-snapshot-folder.md)」をご覧ください  
  
    2.  スナップショット ファイルを既定のフォルダーにも書き込む必要がない限り、 **[ファイルを既定のフォルダーに保存する]** チェック ボックスはオフにしてください。  
  
        > [!NOTE]  
        >  このチェック ボックスをオンにした場合、既定のフォルダーに格納されたファイルは圧縮されません。 圧縮されたファイルは、上記の手順で別途指定した場所にのみ格納できます。  
  
2.  **[スナップショット ファイルをこのフォルダーに圧縮]** チェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [スナップショットのプロパティの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md)   
 [圧縮スナップショット](../compressed-snapshots.md)   
 [スナップショットを使用したサブスクリプションの初期化](../initialize-a-subscription-with-a-snapshot.md)  
  
  

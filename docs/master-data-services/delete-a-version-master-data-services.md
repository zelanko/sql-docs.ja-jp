---
title: "バージョンを削除する (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バージョン [マスター データ サービス], 削除"
  - "バージョンの削除 [マスター データ サービス]"
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# バージョンを削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で、バージョンに関連付けられたマスター データが確実に不要になった場合には、そのバージョンを削除します。 バージョンを削除した後、関連するマスター データを取得することはできません。  
  
> [!WARNING]  
>  モデルにバージョンが 1 つしかない場合にそのバージョンを削除すると、モデルは使用できなくなります。  
  
## 前提条件  
 この手順を実行するには  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.viw_SYSTEM_SCHEMA_VERSION ビューを表示して mds.udpVersionDelete ストアド プロシージャを実行するための権限が必要です。 詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](../master-data-services/database-object-security-master-data-services.md)」を参照してください。  
  
### バージョンを削除するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの [!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスに接続します。  
  
2.  mdm.viw_SYSTEM_SCHEMA_VERSION ビューを開きます。  
  
3.  削除するモデルのバージョンを見つけ、**ID** フィールドの値をコピーします。  
  
4.  新しいクエリを作成します。  
  
5.  次のテキストを入力します。その場合、*version_ID* を手順 2 でコピーした値で置き換えます。  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  クエリを実行します。  
  
    > [!NOTE]  
    >  Web アプリケーションに変更が反映されるまで数分かかる場合があります。  
  
## 参照  
 [バージョン (マスター データ サービス)](../master-data-services/versions-master-data-services.md)   
 [バージョンをコピーする (マスター データ サービス)](../master-data-services/copy-a-version-master-data-services.md)  
  
  
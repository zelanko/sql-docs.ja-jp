---
title: "[バックアップ デバイスの選択] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.selectbackupdevice.f1"
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# [バックアップ デバイスの選択]
  **[バックアップ デバイスの選択]** ダイアログ ボックスを使用すると、復元操作で使用する論理バックアップ デバイスを選択できます。  
  
 論理バックアップ デバイスは、オペレーティング システムによって提供される物理デバイス (テープ ドライブまたはディスク ドライブ) に対応するユーザー定義の論理デバイスです。  
  
> [!NOTE]  
>  バックアップで複数のバックアップ デバイスを使用する場合、すべてのバックアップ デバイスが 1 つの種類のデバイスに対応する必要があります。  
  
 **SQL Server Management Studio を使用してバックアップ デバイスの内容を表示するには**  
  
-   [バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## オプション  
 **バックアップ デバイス**  
 復元操作で使用する論理バックアップ デバイスの名前を、このリスト ボックスから選択します。  
  
 バックアップデバイスのコンテンツの表示方法の詳細については、「[論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)」を参照してください。  
  
## 解説  
 探していたバックアップを含む論理バックアップ デバイスが一覧に表示されない場合、バックアップが 1 つ以上のファイルまたはテープ ドライブに直接書き込まれている可能性があります。 この場合、 **[バックアップ デバイスの選択]** ダイアログ ボックスを取り消し、 **[バックアップの指定]** ダイアログ ボックスの **[バックアップ メディア]** ボックスで **[ファイル]** または **[テープ]** を選択します。  
  
## 参照  
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  
---
title: "データベースのファイルの瞬時初期化 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 940f322fb3afe4b7bfff35f0b25b7b7605452a27
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="database-instant-file-initialization"></a>データベースのファイルの瞬時初期化
  データおよびログ ファイルの初期化は、ディスクに以前削除したファイルのデータが残っている場合にそれを上書きするために行います。 データおよびログ ファイルは、次のいずれかの操作を実行したときに、ファイルを 0 で埋め込むことにより、まず初期化されます。  
  
-   データベースの作成。  
  
-   既存のデータベースへのファイル、ログまたはデータの追加。  
  
-   既存のファイルのサイズを大きくする (自動拡張操作を含む)。  
  
-   データベースまたはファイル グループの復元。  
  
 上記の操作は、ファイルの初期化によって余分な時間がかかります。 ただし、データを初めてファイルに書き込む際には、オペレーティング システムがファイルを 0 で埋め込む必要はありません。  
  
## <a name="instant-file-initialization"></a>ファイルの瞬時初期化  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、データ ファイルを瞬時に初期化できます。 これにより、上記のファイル操作を高速に実行することが可能になります。 ファイルの瞬時初期化では、0 で埋め込むことなく、使用中のディスク領域の返還を要求します。 代わりに、新しいデータがファイルに書き込まれるときに、ディスクの内容が上書きされます。 ログ ファイルを瞬時に初期化することはできません。  
  
> [!NOTE]  
>  ファイルの瞬時初期化は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] または [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 以降のバージョンでのみ使用できます。  
  
 ファイルの瞬時初期化は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) サービス アカウントに SE_MANAGE_VOLUME_NAME が許可されている場合にのみ有効です。 Windows Administrator グループのメンバーにはこの権限があり、他のユーザーを **ボリュームの保守タスクを実行** セキュリティ ポリシーに追加することにより、これらのユーザーにこの権限を許可することができます。 ユーザー権利の割り当ての詳細については、Windows のマニュアルを参照してください。  
  
 ファイルの瞬時初期化は、TDE が有効になっている場合は使用できません。  
  
 アカウントに `Perform volume maintenance tasks` 権限を許可する方法。  
  
1.  バックアップ ファイルを作成するコンピューター上で、 **ローカル セキュリティ ポリシー** アプリケーション (`secpol.msc`) を開きます。  
  
2.  左側のペインで **[ローカル ポリシー]**を展開し、 **[ユーザー権利の割り当て]**をクリックします。  
  
3.  右側のペインで、 **[ボリュームの保守タスクを実行]**をダブルクリックします。  
  
4.  **[ユーザーまたはグループの追加]** をクリックし、バックアップに使用される任意のユーザー アカウントを追加します。  
  
5.  **[適用]**をクリックし、 **[ローカル セキュリティ ポリシー]** ダイアログ ボックスをすべて閉じます。  
  
### <a name="security-considerations"></a>セキュリティに関する考慮事項  
 削除されたディスクの内容は、新しいデータがファイルに書き込まれるときにのみ上書きされるため、許可されていないプリンシパルがこの削除された内容にアクセスする可能性があります。 データベース ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスにアタッチされている間は、ファイル上の任意のアクセス制御リスト (DACL) により、このような情報公開の脅威は低減されます。 この DACL により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントとローカル管理者のみにファイル アクセスが許可されます。 しかし、ファイルがデタッチされると、SE_MANAGE_VOLUME_NAME のないユーザーまたはサービスによりアクセスされる可能性があります。 データベースがバックアップされる際にも、同様の脅威が存在します。 バックアップ ファイルが適切な DACL で保護されていないと、許可されていないユーザーやサービスが削除された内容を利用できるようになる場合があります。  
  
 削除された内容が公開される可能性が懸念される場合は、次のいずれか、または両方を行う必要があります。  
  
-   デタッチされたすべてのデータ ファイルおよびバックアップ ファイルに、常に限定的な DACL が設定されるようにする。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントの SE_MANAGE_VOLUME_NAME を禁止して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対するファイルの瞬時初期化を無効にする。  
  
> [!NOTE]  
>  ファイルの瞬時初期化の無効化で効果があるのは、ユーザー権限が禁止された後で作成またはサイズ増加されたファイルのみです。  
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  

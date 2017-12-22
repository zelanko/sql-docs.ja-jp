---
title: "データベースのファイルの瞬時初期化 | Microsoft Docs"
ms.custom: 
ms.date: 11/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initialization [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
- IFI [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 3f0ef2d2c733a0ab1f349d42d621303cc6c133a5
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="database-file-initialization"></a>データベース ファイルの初期化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] データおよびログ ファイルの初期化は、ディスクに以前削除したファイルのデータが残っている場合にそれを上書きするために行います。 次のいずれかの操作を実行すると、データとログ ファイルは、まずファイルのゼロイング (ゼロを書き込む処理) で初期化されます。  
  
- データベースの作成。  
  
- 既存のデータベースへのデータ ファイルまたはログ ファイルの追加。  
  
- 既存のファイルのサイズを大きくする (自動拡張操作を含む)。  
  
- データベースまたはファイル グループの復元。  
  
上記の操作は、ファイルの初期化によって余分な時間がかかります。 ただし、データを初めてファイルに書き込む際には、オペレーティング システムがファイルを 0 で埋め込む必要はありません。  
  
# <a name="instant-file-initialization-ifi"></a>ファイルの瞬時初期化 (IFI)  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、データ ファイルが瞬時に初期化され、ゼロイング操作を回避できます。 ファイルの瞬時初期化を使うと、上記のファイル操作を高速に実行することが可能になります。 ファイルの瞬時初期化では、0 で埋め込むことなく、使用中のディスク領域の返還を要求します。 代わりに、新しいデータがファイルに書き込まれるときに、ディスクの内容が上書きされます。 ログ ファイルを瞬時に初期化することはできません。  
  
> [!NOTE]  
>  ファイルの瞬時初期化は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] または [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 以降のバージョンでのみ使用できます。  

> [!IMPORTANT]
> ファイルの瞬時初期化は、データ ファイルにのみ使用できます。 ログ ファイルは、作成時やサイズの増大時に常にゼロ化されます。
  
ファイルの瞬時初期化は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス開始アカウントに *SE_MANAGE_VOLUME_NAME* が付与されている場合にのみ使用できます。 Windows Administrator グループのメンバーにはこの権限があり、他のユーザーを **ボリュームの保守タスクを実行** セキュリティ ポリシーに追加することにより、これらのユーザーにこの権限を許可することができます。  
  
[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md) など、ファイルの瞬時初期化を使用できない機能の使用状況もあります。  
  
アカウントに `Perform volume maintenance tasks` 権限を許可する方法。  
  
1.  バックアップ ファイルを作成するコンピューター上で、 **ローカル セキュリティ ポリシー** アプリケーション (`secpol.msc`) を開きます。  
  
2.  左側のペインで **[ローカル ポリシー]**を展開し、 **[ユーザー権利の割り当て]**をクリックします。  
  
3.  右側のペインで、 **[ボリュームの保守タスクを実行]**をダブルクリックします。  
  
4.  **[ユーザーまたはグループの追加]** をクリックし、バックアップに使用される任意のユーザー アカウントを追加します。  
  
5.  **[適用]**をクリックし、 **[ローカル セキュリティ ポリシー]** ダイアログ ボックスをすべて閉じます。  
  
### <a name="security-considerations"></a>セキュリティに関する考慮事項  
 削除されたディスクの内容は、新しいデータがファイルに書き込まれるときにのみ上書きされるため、他のデータがデータ ファイルのその領域に書き込まれるまで、許可されていないプリンシパルが削除された内容にアクセスする可能性があります。 データベース ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスにアタッチされている間は、ファイルに対する随意アクセス制御リスト (DACL) により、このような情報漏えいのリスクは軽減されます。 この DACL により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントとローカル管理者のみにファイル アクセスが許可されます。 ただし、ファイルがデタッチされると、*SE_MANAGE_VOLUME_NAME* が付与されていないユーザーまたはサービスからアクセスされる可能性があります。 データベースのバックアップ時にも同様の懸案事項があります。バックアップ ファイルが適切な DACL で保護されていない場合、許可されていないユーザーやサービスが削除された内容を利用できるようになることがあります。  
 
 セキュリティで保護された環境に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールすると、IFI を有効にしたことによるパフォーマンスの利点が、セキュリティ リスクを上回る可能性があります。それがこの方法をお勧めする理由です。
  
 削除された内容が公開される可能性が懸念される場合は、次のいずれか、または両方の対策を行う必要があります。  
  
- デタッチされたすべてのデータ ファイルおよびバックアップ ファイルに、常に限定的な DACL が設定されるようにする。  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントから *SE_MANAGE_VOLUME_NAME* を失効させて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対するファイルの瞬時初期化を無効にする。  
  
> [!NOTE]  
> ファイルの瞬時初期化の無効化で効果があるのは、ユーザー権限が禁止された後で作成またはサイズ増加されたファイルのみです。  
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  

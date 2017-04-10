---
title: "ロールの割り当て | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ユーザー [Reporting Services]"
  - "ロール [Reporting Services]"
  - "ロールベースのセキュリティ [Reporting Services], ロールの割り当て"
  - "グループ [Reporting Services]"
  - "セキュリティ [Reporting Services], ロールの割り当て"
ms.assetid: 600e112c-1897-48a6-93c0-6e9f3f12dc01
caps.latest.revision: 37
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 37
---
# ロールの割り当て
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、”ロール” の割り当てにより、格納されているアイテムおよびレポート サーバー自体にアクセスできるかどうかが決まります。** ロールの割り当ては以下の要素で構成されています。  
  
-   アクセスを制御するセキュリティ保護可能なアイテム。 セキュリティ保護可能なアイテムの例として、フォルダー、レポート、リソースがあります。  
  
-   Windows セキュリティまたはその他の認証メカニズムにより認証できるユーザー アカウントまたはグループ アカウント。  
  
-   タスクのセットを定義するロールの定義。 ロールの定義の例としては、**システム管理者**、**コンテンツ マネージャー**、**パブリッシャー**があります。  
  
 ロールの割り当ては、フォルダー階層内で継承されます。 あるフォルダーに対して定義されたロールの割り当ては、そのフォルダーに含まれるすべてのレポート、共有データ ソース、リソース、およびサブフォルダーに自動的に継承されます。 個別のアイテムにロールの割り当てを定義することで、継承されるセキュリティを無効にすることができます。 フォルダー階層のすべての部分が、少なくとも 1 つのロールの割り当てによってセキュリティ保護されるようにしてください。 セキュリティで保護されていないアイテムを作成したり、セキュリティで保護されていないアイテムを作成するように設定を操作することはできません。  
  
 フォルダー B に対する**パブリッシャー** ロールにグループおよび特定のユーザーをマップするロールの割り当ての図を次に示します。  
  
 ![ロールの割り当ての図](../../reporting-services/security/media/report-securityarch.gif "ロールの割り当ての図")  
ロールの割り当ての図  
  
## システムレベルおよびアイテムレベルのロールの割り当て  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] におけるロールベースのセキュリティは、次のレベルに分類されます。  
  
-   アイテムレベルのロールの割り当ては、レポート サーバーのフォルダー階層内にあるレポート、フォルダー、レポート モデル、共有データ ソース、およびリソースに対するアクセスを制御します。 アイテムレベルのロールの割り当ては、特定のアイテムまたは [ホーム] フォルダーに対するロールの割り当てを作成するときに定義されます。  
  
-   システム ロールの割り当ては、サーバー全体を対象とする操作を承認します (たとえば、ジョブの管理はシステムレベルの操作です)。 システム ロールの割り当ては、システム管理者と同じではありません。 システム ロールの割り当てでは、レポート サーバーのフル コントロールを許可する権限は付与されません。  
  
 システム ロールの割り当てでは、フォルダー階層内のアイテムに対するアクセスは承認されません。 システムレベルとアイテムレベルのセキュリティは、相互排他的です。 特定のユーザーはまたはグループについて、レポート サーバーに対する十分なアクセスを提供するには、システムレベルとアイテムレベルのロールの割り当てを両方とも作成することが必要になる場合があります。  
  
## ロールの割り当てにおけるユーザーとグループ  
 ロールの割り当てには、ドメイン アカウントであるユーザー アカウントまたはグループ アカウントを指定します。 レポート サーバーからは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ドメイン (カスタム セキュリティ拡張機能を使用している場合は別のセキュリティ モデル) のユーザーおよびグループの参照は行われますが、作成や管理は行われません。  
  
 ある特定のアイテムに適用されるすべてのロールの割り当ての中で、同じユーザーまたはグループを重複して指定することはできません。 あるユーザー アカウントがグループ アカウントのメンバーでもあり、両方のアカウントに対してロールの割り当てを行っている場合、そのユーザーは両方のロールの割り当てに対するタスクを合わせたものを利用できます。  
  
 既にロールの割り当ての一部であるグループにユーザーを追加するとき、そのユーザーに対するロールの割り当てを有効にするには、インターネット インフォメーション サービス (IIS) を再設定する必要があります。  
  
## 定義済みロールの割り当て  
 既定では、ローカル管理者によるレポート サーバーの管理を許可する定義済みのロールの割り当てが実装されます。 ロールの割り当てを追加して、他のユーザーにアクセス権を与える必要があります。  
  
 既定のセキュリティを提供する定義済みのロールの割り当ての詳細については、「[定義済みロール](../../reporting-services/security/predefined-roles.md)」を参照してください。  
  
## 参照  
 [ロールを作成、削除、または変更する (Management Studio)](../../reporting-services/security/create-delete-or-modify-a-role-management-studio.md)   
 [レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)   
 [ロールの割り当てを変更または削除する (レポート マネージャー)](../../reporting-services/security/modify-or-delete-a-role-assignment-report-manager.md)   
 [SharePoint サイト上のレポート サーバー アイテムに対する権限の設定 (Reporting Services の SharePoint 統合モード)](../../reporting-services/security/set permissions for report server items on a sharepoint site.md)   
 [ネイティブ モードのレポート サーバーに対する権限の許可](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
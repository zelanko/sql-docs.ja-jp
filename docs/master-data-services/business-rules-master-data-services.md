---
title: "ビジネス ルール (マスター データ サービス) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
caps.latest.revision: 16
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c8929bcaf6bc937ae6c8bf4bdb0e1b0d2e02f64
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="business-rules-master-data-services"></a>ビジネス ルール (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のビジネス ルールは、マスター データの品質と精度を保証するために使用するルールです。 ビジネス ルールを使用して自動的にデータを更新したり、電子メールを送信したり、ビジネス プロセスまたはワークフローを開始したりできます。  
  
 ビジネス ルールの例を表示するを参照してください。[ビジネス規則の例 & #40 です。マスター データ サービス &#41;](../master-data-services/business-rule-examples-master-data-services.md).  
  
## <a name="create-and-publish-business-rules"></a>ビジネス ルールの作成およびパブリッシュ  
 ビジネス ルールは、 **ssMDSmdm** で作成する [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]ステートメントです。 属性値が特定の条件を満たす場合、アクションが実行されます。それ以外の場合は、Else アクションが実行されます。 実行可能なアクションは、既定値の設定または値の変更です。 これらのアクションを、電子メール通知の送信と組み合わせることができます。  
  
 ビジネス ルールは、特定の属性値に基づいて作成する (たとえば、Color=Blue の場合にアクションを実行する) か、属性値の変更に基づいて作成する (たとえば、Color 属性の値が変更されたときにアクションを実行する) ことができます。 特定されていない変更の追跡の詳細については、次を参照してください。[変更の追跡 (&) #40 です。マスター データ サービス &#41;](../master-data-services/change-tracking-master-data-services.md).  
  
 ビジネス ルールを使用するには、ルールを作成してパブリッシュし、パブリッシュしたルールをデータに適用する必要があります。 バージョンを検証することによって、バージョンのデータのサブセットまたはすべてのデータにルールを適用できます。 バージョンは、すべての属性がビジネス ルール検証に合格するまでコミットできません。  
  
 ビジネス ルール検証に合格していない属性値を追加しようとした場合でも、値は保存されます。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]に表示される検証の問題は、確認して修正できます。  
  
 モデル配置パッケージを作成するときにビジネス ルールを含める場合は、パッケージ内のバージョンからデータを含める必要があります。  
  
 **OR** 演算子を使用するビジネス ルールを作成する場合は、個別に評価できる条件ステートメントごとに個別のルールを作成してください。 そうすることによって、必要に応じてルールを除外できるので、柔軟性が向上し、トラブルシューティングも容易になります。  
  
## <a name="how-business-rules-are-applied"></a>ビジネス ルールの適用方法  
 ビジネス ルールを上下に移動することで、ルールを実行する優先順位を設定できます。 ただし、優先順位が適用される前に、ビジネス ルールはそのルールによって実行されるアクションの種類に基づいて適用されます。 順序は次のとおりです。  
  
1.  **既定値**  
  
2.  **値の変更**  
  
3.  **検証**  
  
4.  **外部アクション**  
  
5.  **ユーザー定義アクション スクリプト**  
  
 これらのグループの中で、アクションが優先順位に基づいて (値が小さいものから順に) 適用されます。 そのため、たとえば別々の 4 つのルールに **既定値** アクションが含まれる場合があります。 最初に実行される **既定値** アクションは、Web UI で指定された優先順位によって決まります。  
  
 ルールの適用については、次の点についても注意してください。  
  
-   ビジネス ルールが除外された場合、または **[アクティブ]**の状態でパブリッシュされていない場合、そのルールは使用可能ですが、ビジネス ルールが適用されるときには対象となりません。  
  
-   ビジネス ルールは、すべてのリーフ メンバーまたはすべての統合メンバーのいずれかの属性値に適用されます。  
  
-   ビジネス ルールは、 **[未処理]** または **[ロック済み]**である、任意のバージョンのモデルに適用できます。  
  
-   ビジネス ルールに適用するときにデータに加えられた変更は、トランザクションとしては記録されません。  
  
-   ビジネス ルールには、 **"がワークフローで始まる"** アクションを複数含めることはできません。  
  
## <a name="system-settings"></a>システム設定  
 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、ビジネス ルールに影響する設定が 2 つあります。 これらの設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するかSystem Settings テーブルで直接調整することができます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|新しいビジネス ルールを作成してパブリッシュする。|[作成して発行するビジネス ルール & #40 です。マスター データ サービス &#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|ビジネス ルールに複数の条件を追加する。|[ビジネス ルール &#40; に複数の条件を追加します。マスター データ サービス &#41;](../master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|属性が値を持つことを必須とするビジネス ルールを作成する。|[属性値 &#40; が必要マスター データ サービス &#41;](../master-data-services/require-attribute-values-master-data-services.md)|  
|属性値の変更に基づくアクションを行うためのビジネス ルールを作成する。|[属性値の変更 &#40; に基づいてアクションを開始します。マスター データ サービス &#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|ユーザー定義のスクリプトを条件として実行するビジネス ルールを作成する|[ビジネス ルールの拡張機能と #40 です。マスター データ サービス &#41;](../master-data-services/business-rules-extension-master-data-services.md)|  
|ユーザー定義のスクリプトをアクションとして実行するビジネス ルールを作成する|[ビジネス ルールの拡張機能と #40 です。マスター データ サービス &#41;](../master-data-services/business-rules-extension-master-data-services.md)|  
|既存のビジネス ルールの名前を変更する。|[ビジネス ルールの名前 &#40; を変更します。マスター データ サービス &#41;](../master-data-services/change-a-business-rule-name-master-data-services.md)|  
|ビジネス ルールが適用されたときに通知を送信するように [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を構成する。|[通知 &#40; を送信するビジネス ルールを構成します。マスター データ サービス &#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|特定のメンバーにビジネス ルールを適用する。|[ビジネス ルール &#40; に対して特定のメンバーを検証します。マスター データ サービス &#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|ビジネス ルールを除外して、使用されないようにする。|[ビジネス ルール &#40; を除外します。マスター データ サービス &#41;](../master-data-services/exclude-a-business-rule-master-data-services.md)|  
|既存のビジネス ルールを削除する。|[ビジネス ルール &#40; を削除します。マスター データ サービス &#41;](../master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [バージョンと #40 です。マスター データ サービス &#41;](../master-data-services/versions-master-data-services.md)  
  
-   [検証と #40 です。マスター データ サービス &#41;](../master-data-services/validation-master-data-services.md)  
  
-   [変更の追跡 & #40 です。マスター データ サービス &#41;](../master-data-services/change-tracking-master-data-services.md)  
  
  

---
title: SQL Server 2014 で非推奨のマスター データ サービスが機能 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 423e45193aed8d0f499e5920f08f8c8551e27545
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164825"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a>SQL Server 2014 に含まれている非推奨のマスター データ サービス機能
  このトピックでは、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] でまだ使用できるものの、非推奨とされた [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の機能について説明します。 これらの機能は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の今後のリリースで削除される予定です。 非推奨の機能を新しいアプリケーションで使用しないでください。  
  
## <a name="staging-process"></a>ステージング処理  
 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で使用されていたステージング処理は、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションでは使用できなくなりましたが、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] では引き続き使用できます。  
  
 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] のステージング処理のステージング エラーは、UI に表示されなくなります。 ステージング処理中に設定されるエラー コードは、ステージング テーブルで使用できることをご覧ください: [ http://msdn.microsoft.com/library/ff487022.aspx](http://msdn.microsoft.com/library/ff487022.aspx)です。  
  
 ステージング テーブル (tblStgMember、tblStgMemberAttribute、および tblStgRelationship) は、データベースで引き続き使用できます。 ステージング処理 (mdm.udpStagingSweep) を起動するために使用していたストアド プロシージャは、データベースで引き続き使用できます。  
  
 ステージング処理を呼び出す web サービス メソッドは引き続き使用できます。  
  
 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]で設定するステージングの間隔は、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] および [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の両方のステージング処理に適用されます。  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] には、新しくパフォーマンスの高いステージング処理が実装されています。 詳細については、「[データのインポート &#40;マスター データ サービス&#41;](overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
## <a name="metadata"></a>メタデータ  
 メタデータ モデルは[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションに引き続き表示されますが、使用しないでください。 将来のリリースでは削除される予定です。 ユーザーも表示できなくなります内のメタデータ、**エクスプ ローラー**  機能領域とすることができます、メタデータ モデルのバージョンを作成できなくします。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 で提供が中止されたマスター データ サービス機能](discontinued-master-data-services-features.md)  
  
  
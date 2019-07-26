---
ms.openlocfilehash: 2dc81d434714e0a13912fa6f14e1194df5e5afe3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215610"
---
> [!NOTE]
> リソースを作成すると、以降は定期的に、可用性グループの構成に基づいて可用性グループの `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` の値を Pacemaker リソース エージェントが自動的に設定します。 たとえば、可用性グループに 3 つの同期レプリカがある場合、エージェントは `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` を `1` に設定します。 詳細およびその他の構成オプションについては、「[High availability and data protection for availability group configurations](../linux/sql-server-linux-availability-group-ha.md)」 (可用性グループ構成の高可用性とデータ保護) を参照してください。 
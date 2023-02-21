

계정정보 상세보기 API 를 만들었음



@Transactional
    override fun detailAccountInfo(accountInfoSeq: Long): AccountInfoDetailDTO {
        accountInfoSeq.let { 
            val accountInfo: AccountInfo = accountInfoRepository.findById(accountInfoSeq).orElseThrow()
            return AccountInfoDetailDTO( //JPA findbyid 를 사용하여 seq 값으로 객체를 가져와서 상세정보를 dto로 변환해서 return 하도록 변경함.
                accountInfo.accountInfoSeq,
                accountInfo.riotUserKey,
                accountInfo.encryptAccountId,
                accountInfo.profileIconId,
                accountInfo.revisionDate,
                accountInfo.nickname,
                accountInfo.puuid,
                accountInfo.summonerLevel,
                accountInfo.leagueInfo
            )
        }
    }

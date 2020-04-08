1. Make sure database have optimal indexes especially on tables:
    - jobs
    - affiliates

2. Change 'where like or' to 'full text index'
    From: (Line 97) 
        (JobCategories.name LIKE '%キャビンアテンダント%'
        OR JobTypes.name LIKE '%キャビンアテンダント%'
        OR Jobs.name LIKE '%キャビンアテンダント%'
        OR Jobs.description LIKE '%キャビンアテンダント%'
        OR Jobs.detail LIKE '%キャビンアテンダント%'
        OR Jobs.business_skill LIKE '%キャビンアテンダント%'
        OR Jobs.knowledge LIKE '%キャビンアテンダント%'
        OR Jobs.location LIKE '%キャビンアテンダント%'
        OR Jobs.activity LIKE '%キャビンアテンダント%'
        OR Jobs.salary_statistic_group LIKE '%キャビンアテンダント%'
        OR Jobs.salary_range_remarks LIKE '%キャビンアテンダント%'
        OR Jobs.restriction LIKE '%キャビンアテンダント%'
        OR Jobs.remarks LIKE '%キャビンアテンダント%'
        OR Personalities.name LIKE '%キャビンアテンダント%'
        OR PracticalSkills.name LIKE '%キャビンアテンダント%'
        OR BasicAbilities.name LIKE '%キャビンアテンダント%'
        OR Tools.name LIKE '%キャビンアテンダント%'
        OR CareerPaths.name LIKE '%キャビンアテンダント%'
        OR RecQualifications.name LIKE '%キャビンアテンダント%'
        OR ReqQualifications.name LIKE '%キャビンアテンダント%')
    To: 
        MATCH(JobCategories.name,JobTypes.name,Jobs.name,Jobs.description,Jobs.detail,Jobs.business_skill,Jobs.knowledge,Jobs.location,Jobs.activity,Jobs.salary_statistic_group,Jobs.salary_range_remarks,Jobs.restriction,Jobs.remarks,Personalities.name,PracticalSkills.name,BasicAbilities.name,Tools.name,CareerPaths.name,RecQualifications.name) AGAINST('キャビンアテンダント')

    Note: 
        - By using Full Text Index, full text search uses the match(field) against('text') syntax. Its avoiding using LIKE seach with leading wildcard where it will not use an index when searching the record.
        - optimal indexes 


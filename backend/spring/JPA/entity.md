### Entity

#### 연관관계 설정

1. 1:N 관계
   member
   ```kt
   @OneToMany(mappedBy = "member")
   var order: List<Order> = arrayListOf()
   ```
   order
   ```kt
   @ManyToOne
   @JoinColumn(name = "member_id")
   var member: Member = null
   ```
   - order와 member중 어느 값이 변경되었을 때 FK를 변경할지 정하기 위해 연관관계 주인을 설정해야함
   - FK에 가까운 쪽이 연관관계 주인임, order테이블에서 member_id(FK)를 가지고 있으므로 연관관계의 주인임

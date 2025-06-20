
## Tech Stack

- **Next JS**
- **Tailwind**
- **Redux Toolkit**
- **Redux Toolkit Query**
- **Material UI Data Grid**
- **Node.js**
- **Prisma**
- **AWS EC2**
- **AWS RDS**
- **AWS API Gateway**
- **AWS Amplify**
- **AWS S3**

## Resources and Links

### Configuration and Code

- [tailwind.config.ts](https://github.com/HenryCode4/inventory-management/blob/master/client/tailwind.config.ts) (to copy)
- [Redux store file](https://github.com/HenryCode4/inventory-management/blob/master/client/src/app/redux.tsx) (to copy)
- [Seed files for database](https://github.com/HenryCode4/inventory-management/blob/master/server/prisma/seed.ts) (to copy)
- [Seed data files](https://github.com/HenryCode4/inventory-management/tree/master/server/prisma/seedData) (to download)

### Additional Resources

- [Data model diagram](https://drawsql.app/teams/team-3023/diagrams/56-inventorymanagement)
- [Prisma schema file](https://github.com/HenryCode4/inventory-management/blob/master/server/prisma/schema.prisma)
- [AWS commands](https://github.com/HenryCode4/inventory-management/blob/master/server/aws-ec2-instructions.md)

npm i prisma @prisma/client
npx prisma init

npx prisma generate
npx prisma migrate dev --name init

npm run seed

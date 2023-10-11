NextJS Image Gallery using MongoDB(mongoose) + Nextjs Server Actions + Pure CSS + Next-Auth + Cloudinary

I. Main functions.    
  - SignIn with OAuth ( Google )     
  - Update Profile        
  - Middleware to secure certain pages         
  - Upload multiple photos       
  - Get all public photos        
  - Paginate by _id and updatedAt        
  - Search (photos + users)        
  - Favorite photo         
  - Follow user        
  - Get all followings and followes by user        
  - Get all public, private, favorite photos by user          
  - Show modal photo by _id           
  - Download image        


II. Implementation Guide.       

1. Setup     
  - npx create-next-app@latest      
  - npm i mongoose next-auth cloudinary react-toastify         
  - next.config.js      
    + experimental: {       
        serverActions: true      
      },         
      images: {         
        domains: ['lh3.googleusercontent.com', 'res.cloudinary.com'],           
      }           
  - layout.js + globals.css         

2. Setup Database      
  - .env => MONGODB_URI        
  - utils=> database.js        
  - models => userModel + photoModel         

3. Next Auth        
  - .env => NEXTAUTH_URL, NEXTAUTH_SECRET, GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET       
  - app/api/auth/[...nextauth]        
    + Google Login        
  - provider => AuthProvider.js        
  - layout => AuthProvider, Nav, head (google icons)          

4. NavBar + SearchForm + getServerUser        

5. Header Component         

6. Upload Page        
  - Upload Form       
    + handleChange       
    + handleInputFiles      
    + validFiles         
    + handleDrop        

  - Upload Card        
    + handleChangeTitle         
    + handleInputTags          
    + handleRemoveTag       
    + handleChangePublic         
    + handleRemoveFile         
    + validate         
    
  - handleUpload         
    + uploadPhoto action       
    + uploadPhotosToCloudinary        
    + Generate blurDataURL      
        
7. GetPhotos          
  - Gallery Component          
  - PhotoCard Component          
  - handleDownloadImage          

8. Pagination Infinite Scrolling         
  - next_cursor       
  - LoadMore         
  - hooks => useInView()         

9. Favorite Photo     

10. Profile Page      
  - Profile Info         
    + GetUserByID          
    + followUser          
    + Edit Profile           
    + Modal           
    + updateUser          
    
  - Profile Follow           
    + List of followers         
    + List of followings           
    + getUsers        

  - Profile Menu        
    + getPhotosCount (public, private, favorite)          
    + generatePhotosMatch        
    + generatePhotosCountPipeline         

  - Profile Gallery       
    + generatePhotosPipeline         

11. Edit + Delete Photo        
  - deletePhoto Actions       
  - updatePhoto Actions          


12. Search Page         
  - Setup Search Mongodb Atlas          

  - generatePhotosPipeline          
  - generatePhotosCountPipeline        

  - generateUsersPipeline        
  - generateUsersCountPipeline           

  - Search Menu         
    + getUsersCount         
    + getPhotosCount        

  - Search Photos + Search Users          

13. Photo Detail Page         
  - Modal Photo        
  - handleDownloadImage         
  - favoritePhoto          
  - Share Photo          
  - getPhotoById          
  - generateMetadata         

14. Deploy Vercel        
  - Run build => Test         
  - Upload to Github          
  - Deploy to Vercel            
  - Change domain in dynamicBlurData       
  - Setup .env => NEXTAUTH_URL          
  - Setup Google Cloud Console            
    + ..../api/auth/callback/google           
